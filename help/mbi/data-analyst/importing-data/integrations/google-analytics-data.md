---
title: Erwartete Google Analytics-Daten
description: Erfahren Sie, wie Sie mit Ihren Google Analytics-Metriken interagieren können.
exl-id: db9fdaaa-47a9-4095-b1f8-9b6c74c25b7c
role: Admin, Data Architect, Data Engineer, User
feature: Commerce Tables, Data Warehouse Manager, Data Integration, Data Import/Export
source-git-commit: 6e2f9e4a9e91212771e6f6baa8c2f8101125217a
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 0%

---

# Erwartete [!DNL Google Analytics]

Nachdem Sie eine [!DNL Google Analytics]-Integration verbunden haben, können Sie mit Ihren [!DNL Google Analytics] Metriken *sofort im`Visual Report Builder`* interagieren. Wenn Sie den `Visual Report Builder` eingeben und auf **[!UICONTROL Add a Metric]** klicken, wird eine Reihe von Metriken aus Ihrem [!DNL Google Analytics] in einem Dropdown-Menü direkt unter den Metriken in Ihrem Data Warehouse angezeigt.

Die [!DNL Google Analytics]-Integration ist *live* - dies bedeutet, dass die `Report Builder` Daten von [!DNL Google Analytics] anfordert *sofort* wenn Sie eine Metrik zu Ihrem Bericht hinzufügen. Das bedeutet auch, dass die Metriken, auf die Sie zugreifen können, genau so definiert sind, wie sie sich in [!DNL Google Analytics] befinden, und dass diese Werte nicht in Ihrem [!DNL Commerce Intelligence]-Konto *eingelagert* sondern nur visuell in Ihren Berichten angezeigt werden.

+++Unterstützte Metriken und Dimensionen (Google Analytics 3 oder Universal Analytics)

>[!NOTE]
>
>Am 1. Juli 2023 werden die Daten in den Standardeigenschaften von Universal Analytics ([!DNL Google Analytics] 3) nicht mehr verarbeitet. Sie können Ihre Universal Analytics-Berichte für einen Zeitraum nach dem 1. Juli 2023 anzeigen. Neue Daten fließen jedoch nur in [!DNL Google Analytics] 4-Eigenschaften.

[!DNL Google Analytics] Integrationen in [!DNL Commerce Intelligence] verwenden die [!DNL Google Analytics][ Core-Reporting](https://developers.google.com/analytics/devguides/reporting/core/v3/)API) und unterstützen die folgenden Metriken und Dimensionen.

>[!NOTE]
>
>Um unerwartete oder unsinnige Ergebnisse zu vermeiden, stellen Sie sicher, dass alle verwendeten Dimensionen mit einer oder mehreren Metriken kompatibel sind, die Sie im `Report Builder` verwenden. Sie können ([) ](https://ga-dev-tools.google/dimensions-metrics-explorer/).

## Unterstützte Metriken

| [!DNL Commerce Intelligence] Anzeigename | [!DNL Google Analytics]/Formel |
| --- | --- |
| `Page Views` | `ga:pageviews` |
| `Total Time Spent On Page` | `ga:timeOnPage` |
| `Bounces (One Page Visits)` | `ga:bounces` |
| `Entrances` | `ga:entrances` |
| `Exits` | `ga:exits` |
| `Unique Pageviews` | `ga:uniquePageviews` |
| `Ad Clicks` | `ga:adClicks` |
| `Ad Cost` | `ga:adCost` |
| `Cost per Click (CPC)` | `ga:CPC` |
| `Cost per Thousand Impressions (CPM)` | `ga:CPM` |
| `Click-Through Rate (CTR)` | `ga:CTR` |
| `Impressions` | `ga:impressions` |
| `Product Revenue` | `ga:itemRevenue` |
| `Products Purchased` | `ga:itemQuantity` |
| `Revenue` | `ga:transactionRevenue` |
| `Transactions` | `ga:transactions` |
| `Shipping Revenue` | `ga:transactionShipping` |
| `Tax Revenue` | `ga:transactionTax` |
| `Unique Purchases` | `ga:uniquePurchases` |
| `Pageviews After Internal Search` | `ga:searchDepth` |
| `Visit Duration After Internal Search` | `ga:searchDuration` |
| `Exits After Internal Search` | `ga:searchExits` |
| `Internal Search Refinements` | `ga:searchRefinements` |
| `Unique Users Using Internal Search` | `ga:searchUniques` |
| `Bounce Rate` | `ga:visitBounceRate` |
| `Average Time on Page` | `ga:avgTimeOnPage` |
| `Average Session Length` | `ga:avgSessionDuration` |
| `All Goals Conversion Rate` | `ga:goalConversionRateAll` |
| `Total Events` | `ga:totalEvents` |
| `Unique Events` | `ga:uniqueEvents` |
| `Event Value` | `ga:eventValue` |
| `Average Domain Lookup Time` | `ga:avgDomainLookupTime` |
| `Average Page Download Time` | `ga:avgPageDownloadTime` |
| `Average Page Load Time` | `ga:avgPageLoadTime` |
| `Transactions Per Visit` | `ga:transactionsPerVisit` |
| `Sessions` | `ga:sessions` |
| `Users` | `ga:users` |
| `New Users | ga:newUsers` |
| `Sessions Where Internal Search Used` | `ga:searchSessions` |
| `Goal X Starts` | `ga:goal...Starts` |
| `Goal X Completions` | `ga:goal...Completions` |
| `Goal X Conversion Rate` | `ga:goal...ConversionRate` |
| `Goal X Total Value` | `ga:goal...Value` |
| `All Goal Starts` | `ga:goalStartsAll` |
| `All Goal Completions` | `ga:goalCompletionsAll` |
| `All Goals Conversion Rate` | `ga:goalConversionRateAll` |
| `Total Goal Value` | `ga:goal1ValueAll` |

{style="table-layout:auto"}

## Unterstützte Dimensionen

| [!DNL Commerce Intelligence] Anzeigename | [!DNL Google Analytics]/Formel | Gruppierbar? |
| --- | --- | --- |
| `Ad Content` | `ga:adContent` | `Yes` |
| `Ad Group` | `ga:adGroup` | `Yes` |
| `Matched Search Query` | `ga:adMatchedQuery` | `Yes` |
| `Placement Domain` | `ga:adPlacementDomain` | `Yes` |
| `Placement URL` | `ga:adPlacementUrl` | `Yes` |
| `Affiliation` | `ga:affiliation` | `Yes` |
| `Browser` | `ga:browser` | `Yes` |
| `Browser Version` | `ga:browserVersion` | `Yes` |
| `Campaign` | `ga:campaign` | `Yes` |
| `Continent` | `ga:continent` | `Yes` |
| `Custom Variable 2` | `ga:customVarValue2` | `Yes` |
| `Custom Variable 3` | `ga:customVarValue3` | `Yes` |
| `Custom Variable 5` | `ga:customVarValue5` | `Yes` |
| `Date` | `ga:date` | `No` |
| `Day` | `ga:day` | `No` |
| `Days Since Last Session` | `ga:daysSinceLastSession` | `Yes` |
| `Days Since Referring Campagin` | `ga:daysToTransaction` | `Yes` |
| `Device Category` | `ga:deviceCategory` | `Yes` |
| `Custom Dimension 10` | `ga:dimension10` | `Yes` |
| `Custom Dimension 12` | `ga:dimension12` | `Yes` |
| `Custom Dimension 13` | `ga:dimension13` | `Yes` |
| `Custom Dimension 18` | `ga:dimension18` | `Yes` |
| `Custom Dimension 2` | `ga:dimension2` | `Yes` |
| `Custom Dimension 20` | `ga:dimension20` | `Yes` |
| `Custom Dimension 3` | `ga:dimension3` | `Yes` |
| `Custom Dimension 4` | `ga:dimension4` | `Yes` |
| `Custom Dimension 5` | `ga:dimension5` | `Yes` |
| `Custom Dimension 8` | `ga:dimension8` | `Yes` |
| `Custom Dimension 9` | `ga:dimension9` | `Yes` |
| `Event Action` | `ga:eventAction` | `Yes` |
| `Event Category` | `ga:eventCategory` | `Yes` |
| `Event Label` | `ga:eventLabel` | `Yes` |
| `Exit Page Path` | `ga:exitPagePath` | `Yes` |
| `Flash Version Supported` | `ga:flashVersion` | `Yes` |
| `Hour` | `ga:hour` | `No` |
| `In-Market Segment` | `ga:interestInMarketCategory` | `Yes` |
| `Language` | `ga:language` | `Yes` |
| `Longitude` | `ga:longitude` | `No` |
| `Medium` | `ga:medium` | `Yes` |
| `Metro` | `ga:metro` | `Yes` |
| `Mobile Device Branding` | `ga:mobileDeviceBranding` | `Yes` |
| `Mobile Device Info` | `ga:mobileDeviceInfo` | `Yes` |
| `Month` | `ga:month` | `No` |
| `Operating System` | `ga:operatingSystem` | `Yes` |
| `Operating System Version` | `ga:operatingSystemVersion` | `Yes` |
| `Pages Viewed per Session` | `ga:pageDepth` | `Yes` |
| `Page Path` | `ga:pagePath` | `Yes` |
| `Product Category` | `ga:productCategory` | `Yes` |
| `Product Name` | `ga:productName` | `Yes` |
| `Referral URL` | `ga:referralPath` | `No` |
| `Region (State)` | `ga:region` | `Yes` |
| `Screen Colors` | `ga:screenColors` | `Yes` |
| `Screen Resolution` | `ga:screenResolution` | `Yes` |
| `Internal Search Category` | `ga:searchCategory` | `Yes` |
| `Internal Search Refined Keyword(s)` | `ga:searchKeywordRefinement` | `Yes` |
| `Internal Search Used?` | `ga:searchUsed` | `Yes` |
| `Second Page Path` | `ga:secondPagePath` | `Yes` |
| `Source` | `ga:source` | `Yes` |
| `Sub-Continent` | `ga:subContinent` | `Yes` |
| `Transaction ID` | `ga:transactionId` | `Yes` |
| `Custom (User Defined) Value` | `ga:userDefinedValue` | `Yes` |
| `Year` | `ga:year` | `No` |

{style="table-layout:auto"}

+++

+++Unterstützte Metriken und Dimensionen (Google Analytics 4)

[!DNL Google Analytics] Integrationen in verwenden [!DNL Commerce Intelligence] die [!DNL Google Analytics]Data [ v1 (GA4)](https://developers.google.com/analytics/devguides/reporting/data/v1).

>[!NOTE]
>
> Commerce Intelligence unterstützt die folgenden Dimensionen nicht: `cohort`, `cohortNthDay`, `cohortNthMonth` und `cohortNthWeek`.
>
>Um unerwartete oder unsinnige Ergebnisse zu vermeiden, stellen Sie sicher, dass alle verwendeten Dimensionen mit einer oder mehreren Metriken kompatibel sind, die Sie im `Visual Report Builder` verwenden. Sie können den [GA4-Dimensionen- und Metrik-Explorer](https://ga-dev-tools.google/ga4/dimensions-metrics-explorer/) überprüfen.

+++
