# Patch Report: Policy Inquiry v1.1.0
**Generated:** 2026-04-28 02:32:30  
**Source YAML:** `Policy_Inquiry_V1.1.0.yaml`  
**Patched YAML:** `Policy_Inquiry_V1.1.0_patched.yaml`  
**Version Intent:** DRAFT  
**Pre-patch Score:** 84/100 (FAIL)  
**Schemas Modified:** 12 | **Schemas Added:** 28  

---

## Extraction Summary

| Section | DD Fields | YAML Blocks | Schemas Extracted |
|---------|-----------|-------------|-------------------|
| Summary | 2 | 1 | 1 |
| Values | 33 | 1 | 7 |
| Funds | 85 | 1 | 6 |
| Parties | 8 | 1 | 3 |
| Producer | 2 | 1 | 1 |
| Dates | 14 | 1 | 2 |
| Payouts | 22 | 1 | 9 |
| Underlying Assets | 22 | 1 | 2 |
| Systematic Programs | 5 | 1 | 5 |
| Riders | 5 | 1 | 4 |
| Transactions | 28 | 1 | 4 |

---

## Merge Details

### Modified Schemas
- **PolicySummary**: +2 properties (`policyNumber`, `associatedFirmId`)
- **PolicyValue**: +2 properties (`policyNumber`, `associatedFirmId`)
- **PolicyFunds**: +2 properties (`policyNumber`, `associatedFirmId`)
- **PartiesList**: +2 properties (`policyNumber`, `associatedFirmId`)
- **Party**: +2 properties (`partyStatus`, `partyRole`)
- **PolicyProducers**: +2 properties (`policyNumber`, `associatedFirmId`)
- **PolicyDates**: +2 properties (`policyNumber`, `associatedFirmId`)
- **PayoutsList**: +2 properties (`policyNumber`, `associatedFirmId`)
- **UnderlyingAssets**: +3 properties (`policyNumber`, `associatedFirmId`, `transactionId`)
- **SystematicProgramsList**: +2 properties (`policyNumber`, `associatedFirmId`)
- **RidersList**: +2 properties (`policyNumber`, `associatedFirmId`)
- **TransactionsList**: +17 properties (`policyNumber`, `associatedFirmId`, `types`, `limit`, `transactionId`, `originalTransactionId`, `partyPolicyChangeReferenceId`, `partyPolicyNewReferenceId`, `parentId`, `transactionType`, `requestDate`, `processDate`, `reversalDate`, `transactionReason`, `isReverseInitiated`, `version`, `transactionAmounts`)

### New Schemas
- **AccountValues** (12 properties): `beginningAccountValue`, `endingAccountValue`, `minimumRequiredAccountValue`, `unloanedPortionOfAccountValue`, `loanedPortionOfAccountValue`, `surrenderValue`, `surrenderValueWithoutMarketValueAdjustment`, `guaranteedCashSurrenderValueFixed`...
- **LoanValues** (9 properties): `totalLoanBalance`, `totalLoanPrincipal`, `loanPayoffAmount`, `maximumLoanAmount`, `minimumLoanAmount`, `totalLoanAccruedInterest`, `lastLoanInterestDueDate`, `totalNumberOfLoan`...
- **WithdrawalValues** (6 properties): `totalWithdrawalAmount`, `freeWithdrawalAmount`, `yearToDateFreeWithdrawalAmount`, `minimumWithdrawalAmount`, `maximumWithdrawalAmount`, `freeAvailableAmount`
- **MarketValueAdjustment** (1 properties): `isMarketValueAdjusted`
- **RmdInfo** (2 properties): `rmdTaxYear`, `totalRMDAmountRemaining`
- **AuthorizationTransaction** (1 properties): `administrativeTransaction`
- **Fund** (56 properties): `fundAccountType`, `fundId`, `fundName`, `fundPrice`, `fundValuationDate`, `generalLedgerFundCode`, `totalFundValue`, `interestGuaranteedPeriod`...
- **RateTier** (3 properties): `indexReturnPercent`, `tieredRate`, `rateType`
- **FundSegment** (18 properties): `segmentId`, `fundId`, `originalDepositAmount`, `originalDepositDate`, `depositDate`, `depositAmount`, `currentAmount`, `renewalDate`...
- **RateLockInfo** (4 properties): `rateType`, `lockStartDate`, `lockEndDate`, `lockPeriod`
- **TransferRestrictInfo** (1 properties): `fundRestrictReason`
- **PolicyDate** (12 properties): `policyStartDate`, `applicationDate`, `applicationReceivedDate`, `issueDate`, `policyDeliveryDate`, `previousPolicyAnniversaryDate`, `previousPolicyMonthiversaryDate`, `nextAnniversaryDate`...
- **IncomeArrangement** (3 properties): `incomeArrangementId`, `annuitization`, `incomePayments`
- **Annuitization** (6 properties): `isAnnuitized`, `annuitizationStartDateTime`, `annuitizationEndDateTime`, `annuitizationTypeCode`, `periodCertain`, `survivorReduction`
- **PeriodCertain** (1 properties): `numberOfPayments`
- **SurvivorReduction** (2 properties): `primaryreductionCode`, `jointreductionCode`
- **IncomePayment** (5 properties): `incomePaymentId`, `frequencyCode`, `amount`, `adjustments`, `taxExclusion`
- **PaymentAmount** (2 properties): `value`, `amountCode`
- **PaymentAdjustments** (1 properties): `increasePercentage`
- **TaxExclusion** (1 properties): `value`
- **UnderlyingAsset** (19 properties): `insuranceActivityFundID`, `insuranceActivityFundAmount`, `insuranceActivityFundAmountDebitCreditIndicator`, `insuranceActivityFundUnitAmount`, `insuranceActivityFundUnitAmountDebitCreditIndicator`, `insuranceActivityFundUnitPriceAmount`, `insuranceProductSubAccountProductFullName`, `insuranceProductSubAccountAssetClassCode`...
- **SystematicProgramParty** (1 properties): `partyRole`
- **TaxWithholdingParty** (2 properties): `IndividualParty`, `EntityParty`
- **RiderParticipant** (1 properties): `insuredAgeAtIssue`
- **RiderCharge** (2 properties): `riderExerciseCharge`, `riderExerciseChargeRate`
- **Transaction** (3 properties): `externalIdentifiers`, `charges`, `taxWithholdingInstructions`
- **TransactionExternalIdentifier** (2 properties): `referenceNumber`, `externalTransactionId`
- **TransactionCharge** (5 properties): `chargeType`, `isChargeWaived`, `chargeWaiverReason`, `chargeAmount`, `chargeAppliedRate`

---

## Raw Agent Responses

### Summary (2 fields)

## YAML PATCH for Summary DD Fields

```yaml
components:
  schemas:
    PolicySummary:
      type: object
      properties:
        policyNumber:
          type: string
          description: Unique identifier for the policy
        associatedFirmId:
          type: string
          description: Identifier for the firm associated with the policy
        effectiveDate:
          type: string
        cusip:
          type: string
        carrierId:
          type: string
        carrierName:
          type: string
        policyLastRefreshDateTime:
          type: string
        product:
          $ref: '#/components/schemas/Product'
        qualificationType:
          type: string
        policyStatus:
          type: string
        hasRestriction:
          type: boolean
        restrictions:
          type: array
          items:
            $ref: '#/components/schemas/RestrictionReason'
        issueType:
          type: string
        issueState:
          type: string
        currency:
          type: string
      required:
        - policyNumber
        - effectiveDate
        - carrierId
        - policyLastRefreshDateTime
        - product
        - policyStatus
        - issueType
        - currency
```

## Analysis Summary

**SCHEMAS MODIFIED:**
- `PolicySummary`: Added `policyNumber` and `associatedFirmId` properties, updated required array to include `policyNumber`

**SCHEMAS CREATED:**
- None (all fields fit into existing PolicySummary schema)

**FIELD PLACEMENT RATIONALE:**
- `policyNumber`: Added to PolicySummary as it's the primary identifier for policy summary information
- `associatedFirmId`: Added to PolicySummary as it's summary-level metadata about firm association

**TYPE INFERENCE:**
- Both fields inferred as `string` type based on "Id" and "Number" suffixes in DD field names
- `policyNumber` added to required array as it's typically a mandatory identifier
- `associatedFirmId` left optional as firm association may not always be present

**AMBIGUOUS FIELDS:**
- None - both fields clearly belong in the PolicySummary schema based on the DD section name and field semantics

This patch adds the 2 missing Summary DD fields to the existing PolicySummary schema, maintaining OpenAPI 3.1 compliance and following IRI DFA Style Guide conventions.


---

### Values (33 fields)

## YAML PATCH for Values DD Fields

```yaml
components:
  schemas:
    PolicyValue:
      type: object
      properties:
        policyNumber:
          type: string
        associatedFirmId:
          type: string
        valuesAsOfDate:
          type: string
        accountDesignation:
          type: string
        jurisdiction:
          type: string
        sponsoringPlanSeparationDate:
          type: string
        payoutType:
          type: string
        totalDepositITD:
          type: number
        surrenderChargeFreeDate:
          type: string
        digitalPaymentTypeCode:
          type: string
        digitalPaymentTypeDescription:
          type: string
        accountValues:
          $ref: '#/components/schemas/AccountValues'
        loanValues:
          $ref: '#/components/schemas/LoanValues'
        withdrawalValues:
          $ref: '#/components/schemas/WithdrawalValues'
        marketValueAdjustment:
          $ref: '#/components/schemas/MarketValueAdjustment'
        rmdInfo:
          $ref: '#/components/schemas/RmdInfo'
        authorization:
          $ref: '#/components/schemas/Authorization'
      required:
        - policyNumber
        - valuesAsOfDate
        - accountValues
    
    AccountValues:
      type: object
      properties:
        beginningAccountValue:
          type: number
        endingAccountValue:
          type: number
        minimumRequiredAccountValue:
          type: number
        unloanedPortionOfAccountValue:
          type: number
        loanedPortionOfAccountValue:
          type: number
        surrenderValue:
          type: number
        surrenderValueWithoutMarketValueAdjustment:
          type: number
        guaranteedCashSurrenderValueFixed:
          type: number
        guaranteedCashSurrenderValueIndexed:
          type: number
        interestEarned:
          type: number
        totalNetWithdrawalSinceIssue:
          type: number
        totalGainWithdrawnSinceIssue:
          type: number
    
    LoanValues:
      type: object
      properties:
        totalLoanBalance:
          type: number
        totalLoanPrincipal:
          type: number
        loanPayoffAmount:
          type: number
        maximumLoanAmount:
          type: number
        minimumLoanAmount:
          type: number
        totalLoanAccruedInterest:
          type: number
        lastLoanInterestDueDate:
          type: string
          format: date
        totalNumberOfLoan:
          type: integer
        totalYearToDateLoanTaken:
          type: number
    
    WithdrawalValues:
      type: object
      properties:
        totalWithdrawalAmount:
          type: number
        freeWithdrawalAmount:
          type: number
        yearToDateFreeWithdrawalAmount:
          type: number
        minimumWithdrawalAmount:
          type: number
        maximumWithdrawalAmount:
          type: number
        freeAvailableAmount:
          type: number
    
    MarketValueAdjustment:
      type: object
      properties:
        isMarketValueAdjusted:
          type: boolean
    
    RmdInfo:
      type: object
      properties:
        rmdTaxYear:
          type: string
        totalRMDAmountRemaining:
          type: number
    
    AuthorizationTransaction:
      type: object
      properties:
        administrativeTransaction:
          type: array
          items:
            type: string
```

## Analysis Summary

**SCHEMAS MODIFIED:**
- `PolicyValue`: Added `policyNumber` and `associatedFirmId` properties, updated `accountValues`, `loanValues`, `withdrawalValues`, `marketValueAdjustment`, and `rmdInfo` to use proper schema references, added `policyNumber` to required array

**SCHEMAS CREATED:**
- `AccountValues`: New schema containing all account value-related fields from DD
- `LoanValues`: New schema containing all loan value-related fields from DD  
- `WithdrawalValues`: New schema containing all withdrawal value-related fields from DD
- `MarketValueAdjustment`: Enhanced existing object with proper boolean field
- `RmdInfo`: Enhanced existing object with specific RMD fields
- `AuthorizationTransaction`: New schema for authorization transaction fields

**FIELD PLACEMENT RATIONALE:**
- DD dotted paths clearly indicated schema groupings (e.g., `accountValues.*` → AccountValues schema)
- `policyNumber` and `associatedFirmId` added to main PolicyValue schema as top-level identifiers
- `authorizationTransaction.administrativeTransaction` created as separate schema since it doesn't fit existing Authorization schema

**TYPE INFERENCE:**
- Amounts/values/rates → `number` type
- Dates → `string` with `format: date` where applicable  
- Count fields → `integer` type (e.g., `totalNumberOfLoan`)
- Boolean fields with `is` prefix → `boolean` type
- Transaction lists → `array` of strings

**AMBIGUOUS FIELDS:**
- None - all DD dotted paths clearly indicated their schema placement

This patch adds all 33 missing Values DD fields, creating 6 new schemas and modifying 1 existing schema, maintaining OpenAPI 3.1 compliance and following IRI DFA Style Guide conventions.


---

### Funds (85 fields)

## YAML PATCH for Funds DD Fields

```yaml
components:
  schemas:
    PolicyFunds:
      type: object
      properties:
        policyNumber:
          type: string
        associatedFirmId:
          type: string
        startIndex:
          type: integer
        itemsCount:
          type: integer
        totalItemsCount:
          type: integer
        funds:
          type: array
          items:
            $ref: '#/components/schemas/Fund'
      required:
        - policyNumber
    
    Fund:
      type: object
      properties:
        fundAccountType:
          type: string
        fundId:
          type: string
        fundName:
          type: string
        fundPrice:
          type: number
        fundValuationDate:
          type: string
          format: date
        generalLedgerFundCode:
          type: string
        totalFundValue:
          type: number
        interestGuaranteedPeriod:
          type: string
        guaranteedMinimumInterestRate:
          type: number
        assetClass:
          type: string
        carrierCode:
          type: string
        investmentType:
          type: string
        openDate:
          type: string
          format: date
        availableFundsAmount:
          type: number
        capRate:
          type: number
        isTransferSendAllowed:
          type: boolean
        isWithdrawalsAllowed:
          type: boolean
        capAmount:
          type: number
        isTransferDestAllowed:
          type: boolean
        guaranteedInterestRate:
          type: number
        fundRestrictReason:
          type: string
        bonusRate:
          type: number
        financialActivity:
          type: string
        isFinancialActivityReversed:
          type: boolean
        appliesToCoverageId:
          type: string
        arrangementRefId:
          type: string
        financialActivityType:
          type: string
        financialActivityGrossAmount:
          type: number
        financialEffectiveDate:
          type: string
          format: date
        participationRate:
          type: number
        participationDownsideRate:
          type: number
        subAccountTerm:
          type: string
        bufferRate:
          type: number
        capThresholdRate:
          type: number
        floorRate:
          type: number
        mvaRate:
          type: number
        marginRate:
          type: number
        triggerRate:
          type: number
        indexCreditingMethod:
          type: string
        indexCreditingMode:
          type: string
        indexType:
          type: string
        termPeriod:
          type: string
        trackingValue:
          type: number
        initialIndexBenchmarkValue:
          type: number
        currentIndexBenchmarkValue:
          type: number
        minimumCapRate:
          type: number
        indexCreditingDate:
          type: string
          format: date
        isLockFeatureEnabled:
          type: boolean
        indexOptionPeriod:
          type: string
        accruedInterest:
          type: number
        thresholdPercent:
          type: number
        rateTier:
          $ref: '#/components/schemas/RateTier'
        fundSegments:
          type: array
          items:
            $ref: '#/components/schemas/FundSegment'
        rateLockInfo:
          $ref: '#/components/schemas/RateLockInfo'
        transferSendRestrictInfo:
          $ref: '#/components/schemas/TransferRestrictInfo'
        transferDestRestrictInfo:
          $ref: '#/components/schemas/TransferRestrictInfo'
    
    RateTier:
      type: object
      properties:
        indexReturnPercent:
          type: number
        tieredRate:
          type: number
        rateType:
          type: string
    
    FundSegment:
      type: object
      properties:
        segmentId:
          type: string
        fundId:
          type: string
        originalDepositAmount:
          type: number
        originalDepositDate:
          type: string
          format: date
        depositDate:
          type: string
          format: date
        depositAmount:
          type: number
        currentAmount:
          type: number
        renewalDate:
          type: string
          format: date
        numberOfUnits:
          type: number
        sweepAccountId:
          type: string
        interestEarningAmount:
          type: number
        appliedInterestRate:
          type: number
        startingPrice:
          type: number
        startingPriceDate:
          type: string
          format: date
        endingPrice:
          type: number
        endingPriceDate:
          type: string
          format: date
        maxPrice:
          type: number
        maxPriceDate:
          type: string
          format: date
    
    RateLockInfo:
      type: object
      properties:
        rateType:
          type: string
        lockStartDate:
          type: string
          format: date
        lockEndDate:
          type: string
          format: date
        lockPeriod:
          type: string
    
    TransferRestrictInfo:
      type: object
      properties:
        fundRestrictReason:
          type: string
```

## Analysis Summary

**SCHEMAS MODIFIED:**
- `PolicyFunds`: Added `policyNumber` and `associatedFirmId` properties, updated `funds` array to reference new Fund schema, added `policyNumber` to required array

**SCHEMAS CREATED:**
- `Fund`: New comprehensive schema containing all fund-level properties from DD
- `RateTier`: New schema for rate tier information (from `funds.rateTier.*` paths)
- `FundSegment`: New schema for fund segment details (from `funds.fundSegments.*` paths)  
- `RateLockInfo`: New schema for rate lock information (from `funds.rateLockInfo.*` paths)
- `TransferRestrictInfo`: New schema for transfer restriction information (from `funds.transferSendRestrictInfo` and `funds.transferDestRestrictInfo` paths)

**FIELD PLACEMENT RATIONALE:**
- DD dotted paths clearly indicated schema groupings (e.g., `funds.rateTier.*` → RateTier schema)
- `policyNumber` and `associatedFirmId` added to main PolicyFunds schema as top-level identifiers
- All non-dotted fund fields placed in main Fund schema
- Nested objects created based on dotted path prefixes

**TYPE INFERENCE:**
- Amounts/values/rates/percentages → `number` type
- Dates → `string` with `format: date`
- IDs/names/codes/types/methods → `string` type
- Boolean fields with `is` prefix → `boolean` type
- Arrays indicated by plural nouns → `array` type
- Count/index fields → `integer` type

**AMBIGUOUS FIELDS:**
- None - all DD dotted paths clearly indicated their schema placement based on prefixes

This patch adds all 79 missing Funds DD fields, creating 5 new schemas and modifying 1 existing schema, maintaining OpenAPI 3.1 compliance and following IRI DFA Style Guide conventions.


---

### Parties (8 fields)

## YAML PATCH for Parties DD Fields

```yaml
components:
  schemas:
    PartiesList:
      type: object
      properties:
        policyNumber:
          type: string
        associatedFirmId:
          type: string
        startIndex:
          type: integer
        itemsCount:
          type: integer
        totalItemsCount:
          type: integer
        parties:
          type: array
          items:
            $ref: '#/components/schemas/Party'
      required:
        - policyNumber
    
    Party:
      type: object
      properties:
        partyStatus:
          type: string
        partyRole:
          type: string
        paymentForm:
          type: string
        allocationPercentage:
          type: number
        bank:
          $ref: '#/components/schemas/Bank'
        address:
          $ref: '#/components/schemas/Address'
        phones:
          type: array
          items:
            $ref: '#/components/schemas/Phone'
        emails:
          type: array
          items:
            $ref: '#/components/schemas/Email'
        identifications:
          type: array
          items:
            $ref: '#/components/schemas/Identification'
        taxWithholdingInstructions:
          type: array
          items:
            $ref: '#/components/schemas/TaxWithholdingInstruction'
        deathDetails:
          $ref: '#/components/schemas/DeathDetails'
      required:
        - paymentForm
        - allocationPercentage
      oneOf:
        - allOf:
            - properties:
                individualParty:
                  $ref: '#/components/schemas/IndividualParty'
            - required:
                - individualParty
        - allOf:
            - properties:
                entityParty:
                  $ref: '#/components/schemas/EntityParty'
            - required:
                - entityParty
    
    TaxWithholdingInstruction:
      type: object
      properties:
        party:
          oneOf:
            - $ref: '#/components/schemas/IndividualParty'
            - $ref: '#/components/schemas/EntityParty'
        taxWithholdingType:
          type: string
        taxRateToUse:
          type: string
        filingStatus:
          type: string
        dollar:
          type: number
        percentage:
          type: number
        exemptions:
          type: integer
        taxJurisdiction:
          type: string
      required:
        - taxWithholdingType
        - taxRateToUse
```

## Analysis Summary

**SCHEMAS MODIFIED:**
- `PartiesList`: Added `policyNumber` and `associatedFirmId` properties, added `policyNumber` to required array
- `Party`: Added `partyStatus` and `partyRole` properties, implemented polymorphic structure using `oneOf` to support both `IndividualParty` and `EntityParty` types as indicated by DD paths
- `TaxWithholdingInstruction`: Added `party` property with polymorphic support for both `IndividualParty` and `EntityParty` types

**SCHEMAS CREATED:**
- None (all fields fit into existing schemas with modifications)

**FIELD PLACEMENT RATIONALE:**
- `policyNumber` and `associatedFirmId`: Added to PartiesList as top-level identifiers
- `partyStatus` and `partyRole`: Added to Party schema as they are party-level attributes
- `parties.IndividualParty` and `parties.EntityParty`: Implemented as polymorphic structure in Party schema using `oneOf` with `individualParty` and `entityParty` properties
- `parties.taxWithholdingInstructions.party.IndividualParty/EntityParty`: Implemented polymorphic `party` property in TaxWithholdingInstruction schema

**TYPE INFERENCE:**
- Status/role/type fields → `string` type
- Percentage fields → `number` type
- Polymorphic party types → `oneOf` structure referencing existing IndividualParty and EntityParty schemas

**POLYMORPHIC DESIGN DECISIONS:**
- Used `oneOf` with `allOf` structure in Party schema to enforce that exactly one party type must be present
- Used simple `oneOf` in TaxWithholdingInstruction for the party property to allow either party type
- Leveraged existing `IndividualParty` and `EntityParty` schemas rather than creating new ones

**AMBIGUOUS FIELDS:**
- None - DD dotted paths clearly indicated polymorphic relationships and schema placement

This patch adds all 8 missing Parties DD fields by modifying 3 existing schemas with polymorphic support, maintaining OpenAPI 3.1 compliance and following IRI DFA Style Guide conventions for handling party type variations.


---

### Producer (2 fields)

## YAML PATCH for Producer DD Fields

```yaml
components:
  schemas:
    PolicyProducers:
      type: object
      properties:
        policyNumber:
          type: string
        associatedFirmId:
          type: string
        producers:
          type: array
          items:
            $ref: '#/components/schemas/PolicyProducer'
      required:
        - policyNumber
```

## Analysis Summary

**SCHEMAS MODIFIED:**
- `PolicyProducers`: Added `policyNumber` and `associatedFirmId` properties, added `policyNumber` to required array

**SCHEMAS CREATED:**
- None (all fields fit into existing schema with modifications)

**FIELD PLACEMENT RATIONALE:**
- `policyNumber` and `associatedFirmId`: Added to PolicyProducers schema as top-level identifiers that apply to the entire producer collection for a policy
- These fields are not dotted paths, indicating they belong at the root level of the producer data structure
- Consistent with pattern seen in other sections (Funds, Parties) where these same fields were added to their respective top-level schemas

**TYPE INFERENCE:**
- `policyNumber` → `string` type (policy identifier)
- `associatedFirmId` → `string` type (firm identifier)

**REQUIRED FIELDS:**
- Added `policyNumber` to required array as it serves as the primary policy identifier

**AMBIGUOUS FIELDS:**
- None - both fields are clearly top-level identifiers for the producer data structure

This patch adds the 2 missing Producer DD fields by modifying 1 existing schema, maintaining OpenAPI 3.1 compliance and following IRI DFA Style Guide conventions. The changes are minimal and focused, adding only the essential identifier fields needed for policy producer data.


---

### Dates (14 fields)

## YAML PATCH for Dates DD Fields

```yaml
components:
  schemas:
    PolicyDates:
      type: object
      properties:
        policyNumber:
          type: string
        associatedFirmId:
          type: string
        policyDates:
          $ref: '#/components/schemas/PolicyDate'
      required:
        - policyNumber
    
    PolicyDate:
      type: object
      properties:
        policyStartDate:
          type: string
          format: date
        applicationDate:
          type: string
          format: date
        applicationReceivedDate:
          type: string
          format: date
        issueDate:
          type: string
          format: date
        policyDeliveryDate:
          type: string
          format: date
        previousPolicyAnniversaryDate:
          type: string
          format: date
        previousPolicyMonthiversaryDate:
          type: string
          format: date
        nextAnniversaryDate:
          type: string
          format: date
        maturityDate:
          type: string
          format: date
        policyTerminationDate:
          type: string
          format: date
        initialPaymentExpiryDate:
          type: string
          format: date
        nextMonthiversaryDate:
          type: string
          format: date
```

## Analysis Summary

**SCHEMAS MODIFIED:**
- `PolicyDates`: Added `policyNumber` and `associatedFirmId` properties, changed `policyDates` property to reference new PolicyDate schema, added `policyNumber` to required array

**SCHEMAS CREATED:**
- `PolicyDate`: New schema containing all the individual date fields from the `policyDates.*` DD paths

**FIELD PLACEMENT RATIONALE:**
- `policyNumber` and `associatedFirmId`: Added to PolicyDates schema as top-level identifiers
- `policyDates.*` fields: The dotted path prefix clearly indicates these belong in a nested PolicyDate object, so created new PolicyDate schema and updated PolicyDates to reference it
- Consistent with pattern seen in other sections where top-level identifiers are added to the main schema

**TYPE INFERENCE:**
- `policyNumber` and `associatedFirmId` → `string` type (identifiers)
- All `policyDates.*` fields → `string` with `format: date` (all are date fields based on field names ending in "Date")

**REQUIRED FIELDS:**
- Added `policyNumber` to required array as it serves as the primary policy identifier

**SCHEMA DESIGN DECISIONS:**
- Created separate PolicyDate schema rather than embedding all date properties directly in PolicyDates to maintain clean separation and reusability
- Used singular "PolicyDate" for the schema name following style guide convention (schema names are singular)
- All date fields use `string` type with `format: date` following OpenAPI 3.1 conventions

**AMBIGUOUS FIELDS:**
- None - DD dotted paths clearly indicated schema grouping and all field names clearly indicate date types

This patch adds all 14 missing Dates DD fields by modifying 1 existing schema and creating 1 new schema, maintaining OpenAPI 3.1 compliance and following IRI DFA Style Guide conventions for date handling and schema organization.


---

### Payouts (22 fields)

## YAML PATCH for Payouts DD Fields

```yaml
components:
  schemas:
    PayoutsList:
      type: object
      properties:
        policyNumber:
          type: string
        associatedFirmId:
          type: string
        startIndex:
          type: integer
        itemsCount:
          type: integer
        totalItemsCount:
          type: integer
        incomeArrangements:
          type: array
          items:
            $ref: '#/components/schemas/IncomeArrangement'
      required:
        - policyNumber
    
    IncomeArrangement:
      type: object
      properties:
        incomeArrangementId:
          type: string
        annuitization:
          $ref: '#/components/schemas/Annuitization'
        incomePayments:
          type: array
          items:
            $ref: '#/components/schemas/IncomePayment'
    
    Annuitization:
      type: object
      properties:
        isAnnuitized:
          type: boolean
        annuitizationStartDateTime:
          type: string
          format: date-time
        annuitizationEndDateTime:
          type: string
          format: date-time
        annuitizationTypeCode:
          type: string
        periodCertain:
          $ref: '#/components/schemas/PeriodCertain'
        survivorReduction:
          $ref: '#/components/schemas/SurvivorReduction'
    
    PeriodCertain:
      type: object
      properties:
        numberOfPayments:
          type: integer
    
    SurvivorReduction:
      type: object
      properties:
        primaryreductionCode:
          type: string
        jointreductionCode:
          type: string
    
    IncomePayment:
      type: object
      properties:
        incomePaymentId:
          type: string
        frequencyCode:
          type: string
        amount:
          $ref: '#/components/schemas/PaymentAmount'
        adjustments:
          $ref: '#/components/schemas/PaymentAdjustments'
        taxExclusion:
          $ref: '#/components/schemas/TaxExclusion'
    
    PaymentAmount:
      type: object
      properties:
        value:
          type: number
        amountCode:
          type: string
    
    PaymentAdjustments:
      type: object
      properties:
        increasePercentage:
          type: number
    
    TaxExclusion:
      type: object
      properties:
        value:
          type: number
```

## Analysis Summary

**SCHEMAS MODIFIED:**
- `PayoutsList`: Added `policyNumber` and `associatedFirmId` properties, updated `incomeArrangements` array to reference new IncomeArrangement schema, added `policyNumber` to required array

**SCHEMAS CREATED:**
- `IncomeArrangement`: New schema for income arrangement details (from `incomeArrangements.*` paths)
- `Annuitization`: New schema for annuitization information (from `incomeArrangements.annuitization.*` paths)
- `PeriodCertain`: New schema for period certain details (from `incomeArrangements.annuitization.periodCertain.*` paths)
- `SurvivorReduction`: New schema for survivor reduction information (from `incomeArrangements.annuitization.survivorReduction.*` paths)
- `IncomePayment`: New schema for income payment details (from `incomeArrangements.incomePayments.*` paths)
- `PaymentAmount`: New schema for payment amount information (from `incomeArrangements.incomePayments.amount.*` paths)
- `PaymentAdjustments`: New schema for payment adjustments (from `incomeArrangements.incomePayments.adjustments.*` paths)
- `TaxExclusion`: New schema for tax exclusion information (from `incomeArrangements.incomePayments.taxExclusion.*` paths)

**FIELD PLACEMENT RATIONALE:**
- DD dotted paths clearly indicated nested schema structure with multiple levels
- `policyNumber` and `associatedFirmId` added to PayoutsList as top-level identifiers
- Each dotted path prefix created a separate schema to maintain clean separation and reusability
- Arrays indicated by plural nouns (`incomeArrangements`, `incomePayments`) with singular schema names for items

**TYPE INFERENCE:**
- IDs/codes → `string` type
- Amounts/values/percentages → `number` type
- DateTime fields → `string` with `format: date-time`
- Boolean field with `is` prefix → `boolean` type
- Count fields (`numberOfPayments`) → `integer` type
- Arrays indicated by plural nouns → `array` type

**SCHEMA DESIGN DECISIONS:**
- Created separate schemas for each nested object to maintain modularity and reusability
- Used `date-time` format for DateTime fields following OpenAPI 3.1 conventions
- Followed IRI DFA Style Guide with singular schema names and plural array properties
- Preserved exact field names from DD including `primaryreductionCode` and `jointreductionCode` as specified

**AMBIGUOUS FIELDS:**
- None - DD dotted paths clearly indicated schema hierarchy and nesting structure

This patch adds all 22 missing Payouts DD fields by modifying 1 existing schema and creating 8 new schemas, maintaining OpenAPI 3.1 compliance and following IRI DFA Style Guide conventions for complex nested data structures.


---

### Underlying Assets (22 fields)

## YAML PATCH for Underlying Assets DD Fields

```yaml
components:
  schemas:
    UnderlyingAssets:
      type: object
      properties:
        policyNumber:
          type: string
        associatedFirmId:
          type: string
        transactionId:
          type: string
        startIndex:
          type: integer
        itemsCount:
          type: integer
        totalItemsCount:
          type: integer
        underlyingAssets:
          type: array
          items:
            $ref: '#/components/schemas/UnderlyingAsset'
      required:
        - policyNumber
    
    UnderlyingAsset:
      type: object
      properties:
        insuranceActivityFundID:
          type: string
        insuranceActivityFundAmount:
          type: number
        insuranceActivityFundAmountDebitCreditIndicator:
          type: string
        insuranceActivityFundUnitAmount:
          type: number
        insuranceActivityFundUnitAmountDebitCreditIndicator:
          type: string
        insuranceActivityFundUnitPriceAmount:
          type: number
        insuranceProductSubAccountProductFullName:
          type: string
        insuranceProductSubAccountAssetClassCode:
          type: string
        insuranceActivityMutualFundCusipNumber:
          type: string
        insuranceActivityFundMVAAmount:
          type: number
        insuranceActivityFundMVAAmountDebitCreditIndicator:
          type: string
        insuranceActivityFundAdministrativeChargeAmount:
          type: number
        insuranceActivityFundAdministrativeChargeAmountDebitCreditIndicator:
          type: string
        insuranceActivityFundSurrenderChargeAmount:
          type: number
        insuranceActivityFundSurrenderChargeAmountDebitCreditIndicator:
          type: string
        insuranceActivityFundEmployerAmount:
          type: number
        insuranceActivityFundEmployerAmountDebitCreditIndicator:
          type: string
        insuranceActivityFundEmployeeAmount:
          type: number
        insuranceActivityFundEmployeeAmountDebitCreditIndicator:
          type: string
```

## Analysis Summary

**SCHEMAS MODIFIED:**
- `UnderlyingAssets`: Added `policyNumber`, `associatedFirmId`, and `transactionId` properties, updated `underlyingAssets` array to reference new UnderlyingAsset schema, added `policyNumber` to required array

**SCHEMAS CREATED:**
- `UnderlyingAsset`: New schema containing all the individual underlying asset fields from the `underlyingAssets.*` DD paths

**FIELD PLACEMENT RATIONALE:**
- `policyNumber`, `associatedFirmId`, and `transactionId`: Added to UnderlyingAssets schema as top-level identifiers
- `underlyingAssets.*` fields: The dotted path prefix clearly indicates these belong in individual underlying asset objects within the array, so created new UnderlyingAsset schema and updated UnderlyingAssets to reference it
- Consistent with pattern seen in other sections where top-level identifiers are added to the main schema

**TYPE INFERENCE:**
- IDs/codes/names/numbers → `string` type (identifiers, codes, names, CUSIP numbers)
- Amount fields → `number` type (all fields containing "Amount" or "Price")
- Debit/credit indicators → `string` type (indicator fields)

**REQUIRED FIELDS:**
- Added `policyNumber` to required array as it serves as the primary policy identifier

**SCHEMA DESIGN DECISIONS:**
- Created separate UnderlyingAsset schema rather than embedding all properties directly in UnderlyingAssets to maintain clean separation and reusability
- Used singular "UnderlyingAsset" for the schema name following style guide convention (schema names are singular)
- Preserved exact field names from DD as they represent specific insurance industry terminology
- All amount fields use `number` type following OpenAPI 3.1 conventions for monetary values

**FIELD NAMING PATTERNS:**
- Many fields follow the pattern of having both an amount field and a corresponding debit/credit indicator field
- Fields use insurance industry standard naming conventions (e.g., CUSIP numbers, MVA amounts, sub-account terminology)

**AMBIGUOUS FIELDS:**
- None - DD dotted paths clearly indicated schema grouping and field names clearly indicate their purposes and types

This patch adds all 21 missing Underlying Assets DD fields by modifying 1 existing schema and creating 1 new schema, maintaining OpenAPI 3.1 compliance and following IRI DFA Style Guide conventions for financial/insurance data structures.


---

### Systematic Programs (5 fields)

## YAML PATCH for Systematic Programs DD Fields

```yaml
components:
  schemas:
    SystematicProgramsList:
      type: object
      properties:
        policyNumber:
          type: string
        associatedFirmId:
          type: string
        systematicPrograms:
          type: array
          items:
            $ref: '#/components/schemas/SystematicProgram'
      required:
        - policyNumber
    
    SystematicProgram:
      type: object
      properties:
        startIndex:
          type: integer
        itemsCount:
          type: integer
        totalItemsCount:
          type: integer
        arrangementType:
          type: string
        allocationOptionType:
          type: string
        paymentForm:
          type: string
        frequency:
          type: string
        startDate:
          type: string
          format: date
        endDate:
          type: string
          format: date
        previousProgramDate:
          type: string
          format: date
        optedNextProgramDate:
          type: string
          format: date
        nextProgramDate:
          type: string
          format: date
        amountType:
          type: string
        requestedAmount:
          type: number
        requestedPercentage:
          type: number
        externalArrangementId:
          type: string
        numOfModalOccurrences:
          type: integer
        modalAmt:
          type: number
        modalPct:
          type: number
        sourceTransferAmtType:
          type: string
        destTransferAmtType:
          type: string
        arrSource:
          type: string
        arrSubType:
          type: string
        dayOfMonth:
          type: integer
        productCode:
          type: string
        parties:
          type: array
          items:
            $ref: '#/components/schemas/SystematicProgramParty'
        taxWithholdingInstructions:
          type: array
          items:
            $ref: '#/components/schemas/TaxWithholdingInstruction'
    
    SystematicProgramParty:
      type: object
      properties:
        partyRole:
          type: string
    
    TaxWithholdingInstruction:
      type: object
      properties:
        party:
          $ref: '#/components/schemas/TaxWithholdingParty'
    
    TaxWithholdingParty:
      type: object
      properties:
        IndividualParty:
          $ref: '#/components/schemas/IndividualParty'
        EntityParty:
          $ref: '#/components/schemas/EntityParty'
```

## Analysis Summary

**SCHEMAS MODIFIED:**
- `SystematicProgramsList`: Added `policyNumber` and `associatedFirmId` properties, added `policyNumber` to required array
- `SystematicProgram`: Updated `parties` array to reference new SystematicProgramParty schema, updated `taxWithholdingInstructions` array to reference modified TaxWithholdingInstruction schema

**SCHEMAS CREATED:**
- `SystematicProgramParty`: New schema for party information within systematic programs (from `systematicPrograms.parties.*` paths)
- `TaxWithholdingParty`: New schema for party information within tax withholding instructions (from `systematicPrograms.taxWithholdingInstructions.party.*` paths)

**SCHEMAS ENHANCED:**
- `TaxWithholdingInstruction`: Enhanced to include party property referencing TaxWithholdingParty schema

**FIELD PLACEMENT RATIONALE:**
- `policyNumber` and `associatedFirmId`: Added to SystematicProgramsList as top-level identifiers consistent with other sections
- `systematicPrograms.parties.partyRole`: Added to new SystematicProgramParty schema as the dotted path indicates it belongs within individual party objects in the parties array
- `systematicPrograms.taxWithholdingInstructions.party.IndividualParty` and `EntityParty`: Added to new TaxWithholdingParty schema as the dotted paths indicate nested party information within tax withholding instructions

**TYPE INFERENCE:**
- `policyNumber`, `associatedFirmId`, `partyRole` → `string` type (identifiers and role descriptors)
- `IndividualParty` and `EntityParty` → references to existing schemas (these schemas already exist in the spec)

**SCHEMA DESIGN DECISIONS:**
- Created separate SystematicProgramParty schema to handle party-specific information within systematic programs
- Created TaxWithholdingParty schema to handle the polymorphic nature of party information (can be either Individual or Entity)
- Enhanced existing TaxWithholdingInstruction schema to include the party property
- Used references to existing IndividualParty and EntityParty schemas to maintain consistency with the rest of the specification

**POLYMORPHIC DESIGN:**
- TaxWithholdingParty schema allows for either IndividualParty or EntityParty to be present, supporting the flexible party structure indicated by the DD paths

**AMBIGUOUS FIELDS:**
- None - DD dotted paths clearly indicated schema hierarchy and the existing schema names provided clear guidance for references

This patch adds all 5 missing Systematic Programs DD fields by modifying 2 existing schemas and creating 3 new schemas, maintaining OpenAPI 3.1 compliance and following IRI DFA Style Guide conventions for nested data structures and polymorphic party information.


---

### Riders (5 fields)

## YAML PATCH for Riders DD Fields

```yaml
components:
  schemas:
    RidersList:
      type: object
      properties:
        policyNumber:
          type: string
        associatedFirmId:
          type: string
        startIndex:
          type: integer
        itemsCount:
          type: integer
        totalItemsCount:
          type: integer
        riders:
          type: array
          items:
            $ref: '#/components/schemas/Rider'
      required:
        - policyNumber
    
    Rider:
      type: object
      properties:
        timestamp:
          type: string
        riderType:
          type: string
        riderName:
          type: string
        isRiderElected:
          type: boolean
        riderCode:
          type: string
        underwritingStatus:
          type: string
        effectiveDate:
          type: string
          format: date
        exerciseDate:
          type: string
          format: date
        terminationDate:
          type: string
          format: date
        status:
          type: string
        coverageId:
          type: string
        amount:
          type: number
        annualBenefitAmount:
          type: number
        riderBenefitAmount:
          type: number
        riderBenefitPercent:
          type: number
        riderParticipants:
          type: array
          items:
            $ref: '#/components/schemas/RiderParticipant'
        charge:
          $ref: '#/components/schemas/RiderCharge'
        maximumChronicIllnessBenefitPercentage:
          type: number
        maximumPeriodicPaymentPeriod:
          type: string
        riderPaymentDate:
          type: string
          format: date
        remainingBenefit:
          type: number
        isAdditionalBenefitUsedUp:
          type: boolean
        totalBenefit:
          type: number
        payoutOption:
          type: string
        benefitPercent:
          type: number
        annualBenefitLimit:
          type: number
        riderSubType:
          type: string
        livesType:
          type: string
        isParticipantIrrevocable:
          type: boolean
        participantParticipantRoleCode:
          type: string
        additionalRiderClassification:
          type: string
        riderFreeAmt:
          type: number
    
    RiderParticipant:
      type: object
      properties:
        insuredAgeAtIssue:
          type: integer
    
    RiderCharge:
      type: object
      properties:
        riderExerciseCharge:
          type: number
        riderExerciseChargeRate:
          type: number
```

## Analysis Summary

**SCHEMAS MODIFIED:**
- `RidersList`: Added `policyNumber` and `associatedFirmId` properties, added `policyNumber` to required array
- `Rider`: Updated `riderParticipants` array to reference new RiderParticipant schema, updated `charge` property to reference new RiderCharge schema

**SCHEMAS CREATED:**
- `RiderParticipant`: New schema for participant information within riders (from `riders.riderParticipants.*` paths)
- `RiderCharge`: New schema for charge information within riders (from `riders.charge.*` paths)

**FIELD PLACEMENT RATIONALE:**
- `policyNumber` and `associatedFirmId`: Added to RidersList as top-level identifiers consistent with other sections
- `riders.riderParticipants.insuredAgeAtIssue`: Added to new RiderParticipant schema as the dotted path indicates it belongs within individual participant objects in the riderParticipants array
- `riders.charge.riderExerciseCharge` and `riders.charge.riderExerciseChargeRate`: Added to new RiderCharge schema as the dotted paths indicate they belong within the charge object structure

**TYPE INFERENCE:**
- `policyNumber`, `associatedFirmId` → `string` type (identifiers)
- `insuredAgeAtIssue` → `integer` type (age values are typically whole numbers)
- `riderExerciseCharge`, `riderExerciseChargeRate` → `number` type (monetary amounts and rates)

**SCHEMA DESIGN DECISIONS:**
- Created separate RiderParticipant schema to handle participant-specific information within riders, allowing for future expansion of participant properties
- Created separate RiderCharge schema to handle charge-related information within riders, providing clean separation of charge-related fields
- Updated existing Rider schema to use references to the new schemas, maintaining clean object structure
- Used `integer` type for age field as ages are typically whole numbers in insurance contexts
- Used `number` type for charge and rate fields following financial data conventions

**REQUIRED FIELDS:**
- Added `policyNumber` to required array in RidersList as it serves as the primary policy identifier

**STRUCTURAL IMPROVEMENTS:**
- The existing `charge` property in Rider was likely a simple type; now it properly references a structured RiderCharge schema
- The existing `riderParticipants` array now properly references a structured RiderParticipant schema instead of potentially being untyped

**AMBIGUOUS FIELDS:**
- None - DD dotted paths clearly indicated schema hierarchy and field purposes were evident from their names

This patch adds all 5 missing Riders DD fields by modifying 2 existing schemas and creating 2 new schemas, maintaining OpenAPI 3.1 compliance and following IRI DFA Style Guide conventions for nested data structures in insurance rider information.


---

### Transactions (28 fields)

## YAML PATCH for Transactions DD Fields

```yaml
components:
  schemas:
    TransactionsList:
      type: object
      properties:
        policyNumber:
          type: string
        associatedFirmId:
          type: string
        types:
          type: array
          items:
            type: string
        limit:
          type: integer
        transactionId:
          type: string
        originalTransactionId:
          type: string
        partyPolicyChangeReferenceId:
          type: string
        partyPolicyNewReferenceId:
          type: string
        parentId:
          type: string
        transactionType:
          type: string
        requestDate:
          type: string
          format: date
        processDate:
          type: string
          format: date
        reversalDate:
          type: string
          format: date
        transactionReason:
          type: string
        isReverseInitiated:
          type: boolean
        version:
          type: string
        transactionAmounts:
          $ref: '#/components/schemas/TransactionAmounts'
        startIndex:
          type: integer
        itemsCount:
          type: integer
        totalItemsCount:
          type: integer
        transactions:
          type: array
          items:
            $ref: '#/components/schemas/Transaction'
      required:
        - policyNumber
    
    Transaction:
      type: object
      properties:
        externalIdentifiers:
          type: array
          items:
            $ref: '#/components/schemas/TransactionExternalIdentifier'
        charges:
          type: array
          items:
            $ref: '#/components/schemas/TransactionCharge'
        taxWithholdingInstructions:
          type: array
          items:
            $ref: '#/components/schemas/TaxWithholdingInstruction'
    
    TransactionExternalIdentifier:
      type: object
      properties:
        referenceNumber:
          type: string
        externalTransactionId:
          type: string
    
    TransactionCharge:
      type: object
      properties:
        chargeType:
          type: string
        isChargeWaived:
          type: boolean
        chargeWaiverReason:
          type: string
        chargeAmount:
          type: number
        chargeAppliedRate:
          type: number
```

## Analysis Summary

**SCHEMAS MODIFIED:**
- `TransactionsList`: Added 16 new properties including identifiers, dates, flags, and references to existing TransactionAmounts schema, added `policyNumber` to required array

**SCHEMAS CREATED:**
- `Transaction`: New schema for individual transaction objects (from `transactions.*` paths)
- `TransactionExternalIdentifier`: New schema for external identifier information within transactions
- `TransactionCharge`: New schema for charge information within transactions

**FIELD PLACEMENT RATIONALE:**
- Top-level fields (no dotted paths): Added to TransactionsList as they represent list-level metadata and filtering criteria
- `transactions.externalIdentifiers.*`: Added to new TransactionExternalIdentifier schema as the dotted paths indicate nested structure within individual transactions
- `transactions.charges.*`: Added to new TransactionCharge schema as the dotted paths indicate charge-specific information within transactions
- `transactions.taxWithholdingInstructions.party.*`: Reused existing TaxWithholdingInstruction schema (already handles party polymorphism)
- `transactionAmounts`: Referenced existing TransactionAmounts schema

**TYPE INFERENCE:**
- IDs/codes/reasons/types/versions → `string` type
- Dates (requestDate, processDate, reversalDate) → `string` with `format: date`
- Boolean flags (isReverseInitiated, isChargeWaived) → `boolean` type
- Amounts/rates (chargeAmount, chargeAppliedRate) → `number` type
- Limit → `integer` type (typically used for pagination/filtering limits)
- Types → `array` of strings (filter criteria for transaction types)

**SCHEMA DESIGN DECISIONS:**
- Created separate Transaction schema to handle individual transaction objects within the transactions array
- Created TransactionExternalIdentifier schema to handle external reference information
- Created TransactionCharge schema to handle charge-related information with proper boolean flag for waiver status
- Reused existing TaxWithholdingInstruction schema for tax withholding instructions (maintains consistency with other sections)
- Referenced existing TransactionAmounts schema rather than duplicating amount structures

**REQUIRED FIELDS:**
- Added `policyNumber` to required array as it serves as the primary policy identifier

**POLYMORPHIC REUSE:**
- Leveraged existing TaxWithholdingInstruction schema which already handles IndividualParty/EntityParty polymorphism through its party structure

**ARRAY STRUCTURES:**
- `types`: Array of strings for transaction type filtering
- `externalIdentifiers`: Array of TransactionExternalIdentifier objects
- `charges`: Array of TransactionCharge objects
- `taxWithholdingInstructions`: Array of existing TaxWithholdingInstruction objects

**AMBIGUOUS FIELDS:**
- None - DD dotted paths clearly indicated schema hierarchy and field names provided clear type guidance

This patch adds all 28 missing Transactions DD fields by modifying 1 existing schema and creating 3 new schemas, maintaining OpenAPI 3.1 compliance and following IRI DFA Style Guide conventions for complex transactional data structures with proper separation of concerns between list metadata, individual transactions, and nested transaction components.


---
