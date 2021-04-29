##  Billing & Cost Management

[Reff AWS Doc](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/billing-permissions-ref.html)

### Billing and Cost Management console pages :
```
aws-portal:ViewBilling
aws-portal:ModifyBilling
aws-portal:ViewAccount
aws-portal:ModifyAccount
aws-portal:ViewPaymentMethods
aws-portal:ModifyPaymentMethods
aws-portal:ViewUsage
```

### IAM users to view and modify budgets :
```
budgets:ViewBudget
budgets:ModifyBudget
```

### AWS Cost and Usage Reports :
```
cur:DescribeReportDefinitions
cur:PutReportDefinition
cur:DeleteReportDefinition
cur:ModifyReportDefinition
```

### IAM users permission to create/update/delete AWS Cost and Usage Reports :
```
ce:GetPreferences
ce:UpdatePreferences
ce:DescribeReport
ce:CreateReport
ce:UpdateReport
ce:DeleteReport
ce:DescribeNotificationSubscription
ce:CreateNotificationSubscription
ce:UpdateNotificationSubscription
ce:DeleteNotificationSubscription
ce:CreateCostCategoryDefinition
ce:DeleteCostCategoryDefinition
ce:DescribeCostCategoryDefinition
ce:ListCostCategoryDefinitions
ce:UpdateCostCategoryDefinition
ce:CreateAnomalyMonitor
ce:GetAnomalyMonitors
ce:UpdateAnomalyMonitor
ce:DeleteAnomalyMonitor
ce:CreateAnomalySubscription
ce:GetAnomalySubscriptions
ce:UpdateAnomalySubscription
ce:DeleteAnomalySubscription
ce:GetAnomalies
ce:ProvideAnomalyFeedback
```

### IAM users permission to view AWS service products and pricing via the AWS Price List Service API:
```
pricing:DescribeServices
pricing:GetAttributeValues
pricing:GetProducts
```

### IAM users permission to view Purchase Orders:
```
purchase-orders:ViewPurchaseOrders
purchase-orders:ModifyPurchaseOrders
```
