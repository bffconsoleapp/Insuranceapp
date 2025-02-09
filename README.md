```graphql
# schema-codegen-start
const typeDefs = `
  type Credit_Union {
    id: ID!
    Contract_Number: String!
    Credit_Union_Name: String!
    premium_reports: [Premium_Report!]!
    premium_adjustments: [Premium_Adjustment!]!
    single_premium_certificate_returns: [Single_Premium_Certificate_Return!]!
  }

  type Premium_Report {
    id: ID!
  }

  type Premium_Adjustment {
    id: ID!
    Product_Name: String!
    Report_Period: String!
    Status: String!
    Last_Update: String!
    Period_Ending: String!
    Adjustment_Type_to_the_Credit_Union: String!
    Comment: String!
    Total_Borrower_Fees_: Float!
    CU_Retail_Rate: Float!
    Protected_Loan_Amount: Float!
    Pay_Rate: Float!
    Premium_Due: Float!
    Total_Amount: Float!
  }

  type Single_Premium_Certificate_Return {
    id: ID!
  }

  input EditPremiumAdjustmentInput {
    Total_Borrower_Fees: String!
    CU_Retail_Rate: String!
    Protected_Loan_Amount: String!
    Pay_Rate: String!
    Premium_Due: String!
    Total_Amount: String!
  }

  type Query {
    searchCreditUnionByContractNumber(contractNumber: String!): [Credit_Union]
    searchCreditUnionByName(name: String!): [Credit_Union]
    searchCreditUnionByState(state: String!): [Credit_Union]
    searchCreditUnionByNameAndState(name: String!, state: String!): [Credit_Union]
  }

  type Mutation {
    editPremiumAdjustment(id: ID!, input: EditPremiumAdjustmentInput!): Premium_Adjustment
  }
`;
# schema-codegen-end
```

```javascript
// resolver-codegen-start
const resolvers = {
  Query: {
    searchCreditUnionByContractNumber: (_, { contractNumber }) => {
      // Placeholder data
      const creditUnions = [
        {
          id: "1",
          Contract_Number: contractNumber,
          Credit_Union_Name: "Sample Credit Union",
          premium_reports: [],
          premium_adjustments: [],
          single_premium_certificate_returns: [],
        },
      ];
      return creditUnions;
    },
    searchCreditUnionByName: (_, { name }) => {
      const creditUnions = [
        {
          id: "1",
          Contract_Number: "12345",
          Credit_Union_Name: name,
          premium_reports: [],
          premium_adjustments: [],
          single_premium_certificate_returns: [],
        },
      ];
      return creditUnions;
    },
    searchCreditUnionByState: (_, { state }) => {
      const creditUnions = [
        {
          id: "1",
          Contract_Number: "12345",
          Credit_Union_Name: "Sample Credit Union",
          premium_reports: [],
          premium_adjustments: [],
          single_premium_certificate_returns: [],
        },
      ];
      return state ? creditUnions : [];
    },
    searchCreditUnionByNameAndState: (_, { name, state }) => {
      const creditUnions = [
        {
          id: "1",
          Contract_Number: "12345",
          Credit_Union_Name: name,
          premium_reports: [],
          premium_adjustments: [],
          single_premium_certificate_returns: [],
        },
      ];
      return (name && state) ? creditUnions : [];
    },
  },
  Mutation: {
    editPremiumAdjustment: (_, { id, input }) => {
      // Placeholder adjusted premium adjustment
      return {
        id,
        Product_Name: "Sample Product",
        Report_Period: "Q1 2023",
        Status: "Pending",
        Last_Update: "2023-01-01",
        Period_Ending: "2023-03-31",
        Adjustment_Type_to_the_Credit_Union: "Type A",
        Comment: "Sample Comment",
        Total_Borrower_Fees_: parseFloat(input.Total_Borrower_Fees),
        CU_Retail_Rate: parseFloat(input.CU_Retail_Rate),
        Protected_Loan_Amount: parseFloat(input.Protected_Loan_Amount),
        Pay_Rate: parseFloat(input.Pay_Rate),
        Premium_Due: parseFloat(input.Premium_Due),
        Total_Amount: parseFloat(input.Total_Amount),
      };
    },
  },
};
// resolver-codegen-end
```