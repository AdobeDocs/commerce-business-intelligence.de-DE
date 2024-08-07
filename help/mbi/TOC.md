---
title: Commerce Intelligence
description: Erfahren Sie, wie Sie die für Adobe Commerce verfügbaren [!DNL Commerce Intelligence] Funktionen verwenden.
breadcrumb-title: Commerce Intelligence-Benutzerhandbuch
role: Admin, Data Architect, Data Engineer, Leader, User
feature: Business Performance
source-git-commit: 2433a614e9858684842804a0ae29fb67f0d41ead
workflow-type: tm+mt
source-wordcount: '680'
ht-degree: 0%

---


# [!DNL Commerce Intelligence] Benutzerhandbuch {#mbi}

- [[!DNL Commerce Intelligence] Benutzerhandbuch](guide-overview.md)
- [[!DNL Commerce Intelligence] Einführung](getting-started/getting-started.md)
- Erste Schritte {#start}
   - [Onboarding](getting-started/onboarding.md)
   - [Aktivieren Ihres [!DNL Commerce Intelligence] Kontos](getting-started/onpremise-activation.md)
   - [Anmelden bei Ihrem [!DNL Commerce Intelligence] Konto](getting-started/sign-in.md)
   - [Commerce Intelligence Essentials vs. Commerce Intelligence Pro](getting-started/essentials-vs-pro.md)
- Administrator {#administrator}
   - Kontoverwaltung {#acct-mgmt}
      - [Vorteile von [!DNL New Architecture]](../mbi/administrator/account-management/new-architecture.md)
      - [Anzeigen von Dashboards im Büro](../mbi/administrator/account-management/display-dashboards-office.md)
      - [Konto verwalten](administrator/account-management/managing-account-settings.md)
      - [Restrict Database Access](../mbi/administrator/account-management/restrict-db-access.md)
   - Benutzerverwaltung {#user-mgmt}
      - [Benutzer erstellen/bearbeiten](../mbi/administrator/user-management/create-user.md)
      - [Benutzer löschen/reaktivieren](../mbi/administrator/user-management/delete-user.md)
      - [Verwalten von Benutzerberechtigungen](administrator/user-management/user-management.md)
      - [Kennwort zurücksetzen](../mbi/administrator/user-management/reset-password.md)
      - [Zugriff auf Metriken beschränken](../mbi/administrator/user-management/restrict-metric-access.md)
- Daten analysieren {#analyze}
   - [Data Analyst](data-analyst.md)
   - Data Warehouse-Manager {#warehouse-manager}
      - [Einführung](data-analyst/data-warehouse-mgr/tour-dwm.md)
      - [Erweiterte berechnete Spaltentypen](data-analyst/data-warehouse-mgr/adv-calc-columns.md)
      - [Erstellen von [!DNL Google Ecommerce] Dimensionen](data-analyst/data-warehouse-mgr/bldg-google-ecomm-dim.md)
      - [Berechnete Spaltentypen](data-analyst/data-warehouse-mgr/calc-column-types.md)
      - [Konfigurieren von Replikationsmethoden](data-analyst/data-warehouse-mgr/cfg-replication-methods.md)
      - [Konfigurieren von Datenprüfungen](data-analyst/data-warehouse-mgr/cfg-data-rechecks.md)
      - [Ändern der Operationstabelle einer Metrik](data-analyst/data-warehouse-mgr/change-metric-op-table.md)
      - [Erstellen und Verwenden von Data Warehouse-Ansichten](data-analyst/data-warehouse-mgr/create-dw-views.md)
      - [Erstellen/Löschen von Pfaden für berechnete Spalten](data-analyst/data-warehouse-mgr/create-paths-calc-columns.md)
      - [Erstellen/Verwenden einer berechneten SQL-Spalte](data-analyst/data-warehouse-mgr/create-sql-calc-column.md)
      - [Berechnete Spalten erstellen](data-analyst/data-warehouse-mgr/creating-calculated-columns.md)
      - [Daten und Updates - Informationen](data-analyst/data-warehouse-mgr/data-and-updates-faq.md)
      - [Gastaufträge](data-analyst/data-warehouse-mgr/guest-orders.md)
      - [So speichert Commerce Daten](data-analyst/data-warehouse-mgr/mage-store-data.md)
      - [Diagramme zur Entitätsbeziehung](data-analyst/data-warehouse-mgr/entity-rel-diag.md)
      - [Datendimensionen in Metriken verwalten](data-analyst/data-warehouse-mgr/manage-data-dimensions-metrics.md)
      - [[!DNL MongoDB] Datenmodellierungshandbuch](data-analyst/data-warehouse-mgr/mongodb-data-modeling.md)
      - [Replizieren von [!DNL Google Analytics] Kanälen](data-analyst/data-warehouse-mgr/rep-google-analytics-channels.md)
      - [Daten mit Zuordnungstabellen standardisieren](data-analyst/data-warehouse-mgr/stndrd-data-map-tables.md)
      - [SQL-Abfragen in [!DNL Commerce Intelligence] Berichte übersetzen](data-analyst/dev-reports/sql-queries-reports.md)
      - [Verstehen und Auswerten von Tabellenbeziehungen](data-analyst/data-warehouse-mgr/table-relationships.md)
      - [Verwenden der berechneten Datumsdifferenz](data-analyst/data-warehouse-mgr/using-date-diff-calc-column.md)
      - [Verwenden des Dashboard-weiten Filters](data-analyst/data-warehouse-mgr/using-dshbrd-wide-filter-date-ranges.md)
      - [Verwenden der Spalte &quot;Errechnete Ereignisnummer&quot;](data-analyst/data-warehouse-mgr/using-event-num-calc-column.md)
      - [Verwenden der Spalte für den sequenziellen Vergleich der berechneten Werte](data-analyst/data-warehouse-mgr/using-seq-comp-calc-column.md)
   - Allgemeine Commerce-Tabellen {#tables}
      - [Einführung](data-analyst/data-warehouse-mgr/common-mage-tables.md)
      - [[!DNL customer_entity]](data-analyst/data-warehouse-mgr/cust-ent-table.md)
      - [[!DNL enterprise_rma]](data-analyst/data-warehouse-mgr/enter-rma-table.md)
      - [[!DNL enterprise_rma_item_entity]](data-analyst/data-warehouse-mgr/enter-rma-entity-item.md)
      - [[!DNL sales_order]](../mbi/data-analyst/data-warehouse-mgr/sales-flat-order-table.md)
      - [[!DNL sales_order_item]](data-analyst/data-warehouse-mgr/sales-flat-order-item-table.md)
      - [[!DNL quote]](data-analyst/data-warehouse-mgr/sales-flat-quote-table.md)
      - [[!DNL quote_item]](data-analyst/data-warehouse-mgr/sales-flat-quote-item-table.md)
   - SQL-Report Builder {#sql}
      - [Verwenden des  [!DNL Cohort Report Builder]](data-analyst/dev-reports/cohort-rpt-bldr.md)
      - [Verwenden von  [!DNL Cohort Report Builder]  für nicht datumsbasierte Kohorten](data-analyst/dev-reports/cohort-rpt-non-date-based.md)
      - [Erstellen einer qualitativen Kohortenanalyse](data-analyst/dev-reports/create-qual-cohort-analysis.md)
      - [Spezielle Filteroperatoren durchsuchen](data-analyst/dev-reports/explr-special-filter-ops.md)
      - [Ergebnisse meiner Abfrage exportieren](data-analyst/dev-reports/export-query-results.md)
      - [Verwenden von Formeln im [Report Builder]](../mbi/data-analyst/dev-reports/formulas-in-rpt-bldr.md)
      - [Erstellen von [!DNL Google Analytics] Diagrammen](data-analyst/dev-reports/google-analytics-charts-regex.md)
      - [Wichtigkeit von  [!DNL Lifetime Revenue Cohort Analysis]](data-analyst/dev-reports/lifetime-rev-cohort-analysis.md)
      - [Sortieren von Daten mithilfe der [!DNL Show Top/Bottom] Funktion](data-analyst/dev-reports/order-data-top-bottom-feat.md)
      - [Verwenden des  [!DNL SQL Report Builder]](data-analyst/dev-reports/sql-rpt-bldr.md)
      - [Erster Kaufbericht](data-analyst/dev-reports/time-first-purchase-slope-dwnwrd.md)
      - [Grundlegendes zu  [!DNL Repeat Order Probability Report]](data-analyst/dev-reports/repeat-order-probability.md)
      - [Überprüfen von Metriken mit dem  [!DNL SQL Report Builder]](data-analyst/dev-reports/audit-metrics-sql.md)
      - [Unterschiede in Spalten zwischen [!DNL SQL] und [!DNL Data Warehouse Manager]](data-analyst/dev-reports/columns-sql-dwm.md)
   - Verbinden von Daten {#connecting}
      - [Einführung](data-analyst/importing-data/connecting-data/connecting-data.md)
      - [eCommerce-Daten formatieren und importieren](data-analyst/importing-data/connecting-data/format-import-ecom-data.md)
      - [Importieren von [!DNL Bing Ad Spend] Daten](data-analyst/importing-data/connecting-data/import-bing-ad-data.md)
      - [Marketing-Daten importieren [!DNL CJ Affiliate] (Kommissionsfunktion)](data-analyst/importing-data/connecting-data/import-cj-market-data.md)
      - [Importieren von [!DNL Linkshare] Daten](data-analyst/importing-data/connecting-data/import-linkshare-data.md)
      - [Importieren von [!DNL MailChimp] Daten](data-analyst/importing-data/connecting-data/import-mailchimp-data.md)
      - [Importieren von Offline-/anderen Anzeigenausgabedaten](data-analyst/importing-data/connecting-data/import-offline-ad-data.md)
      - [Verwenden des Datei-Uploaders](data-analyst/importing-data/connecting-data/using-file-uploader.md)
      - [Datenmigrationsdienste](data-analyst/importing-data/connecting-data/data-migration-services.md)
   - SaaS-Integrationen {#saas}
      - [SaaS-Integration](data-analyst/importing-data/integrations/integrations.md)
      - [Verstehen der Ergebnisse zwischen [!DNL Database] und [!DNL SQL] Bearbeiter](data-analyst/importing-data/integrations/last-success-update.md)
      - [Verbinden [!DNL Adobe Analytics]](data-analyst/importing-data/integrations/adobe-analytics.md)
      - [Erwartete [!DNL Adobe Analytics] Daten](data-analyst/importing-data/integrations/adobe-analytics-data.md)
      - [Verbinden [!DNL Facebook Ads]](data-analyst/importing-data/integrations/facebook-ads.md)
      - [Erwartete [!DNL Facebook Ads] Daten](data-analyst/importing-data/integrations/facebook-ads-data.md)
      - [Verbinden [!DNL Google Adwords]](data-analyst/importing-data/integrations/google-adwords.md)
      - [Erwartete [!DNL Google Adword] Daten](data-analyst/importing-data/integrations/google-adwords-data.md)
      - [Auditing [!DNL Google Adwords] data](data-analyst/importing-data/integrations/audit-google-adwords.md)
      - [Verbinden [!DNL Google Analytics Warehoused]](data-analyst/importing-data/integrations/google-analytics-warehoused.md)
      - [Erwartete [!DNL Google Analytics Warehoused] Daten](data-analyst/importing-data/integrations/google-analytics-warehoused-data.md)
      - [Verbinden [!DNL Google Analytics]](data-analyst/importing-data/integrations/google-analytics.md)
      - [Erwartete [!DNL Google Analytics] Daten](data-analyst/importing-data/integrations/google-analytics-data.md)
      - [Verbinden [!DNL Google ECommerce]](data-analyst/importing-data/integrations/google-ecommerce.md)
      - [Erwartete [!DNL Google ECommerce] Daten](data-analyst/importing-data/integrations/google-ecommerce-data.md)
      - [Verbinden [!DNL Mixpanel]](data-analyst/importing-data/integrations/mixpanel.md)
      - [Erwartete [!DNL Mixpanel] Daten](data-analyst/importing-data/integrations/mixpanel-data.md)
      - [Datenvalidierung in [!DNL Mixpanel]](data-analyst/importing-data/integrations/mixpanel-data-valid.md)
      - [Verbinden [!DNL PrestaShop]](data-analyst/importing-data/integrations/prestashop.md)
      - [Verbinden [!DNL Quickbooks]](data-analyst/importing-data/integrations/quickbooks.md)
      - [Erwartete [!DNL Quickbooks] Daten](data-analyst/importing-data/integrations/quickbooks-data.md)
      - [Verbinden [!DNL Salesforce]](data-analyst/importing-data/integrations/salesforce.md)
      - [Erwartete [!DNL Salesforce] Daten](data-analyst/importing-data/integrations/salesforce-data.md)
      - [Verbinden [!DNL Spree]](data-analyst/importing-data/integrations/spree.md)
      - [Erwartete [!DNL Spree] Daten](data-analyst/importing-data/integrations/spree-data.md)
      - [Verbinden [!DNL Stripe]](data-analyst/importing-data/integrations/stripe.md)
      - [Erwartete [!DNL Stripe] Daten](data-analyst/importing-data/integrations/stripe-data.md)
      - [Verbinden [!DNL WooCommerce]](data-analyst/importing-data/integrations/woocommerce.md)
      - [Verbinden [!DNL Zendesk]](data-analyst/importing-data/integrations/zendesk.md)
      - [Erwartete [!DNL Zendesk] Daten](data-analyst/importing-data/integrations/exp-zendesk-data.md)
      - [Analysieren von [!DNL Zendesk] Daten](data-analyst/importing-data/integrations/help-desk-zendesk.md)
      - [Auditing [!DNL Zendesk] data](data-analyst/importing-data/integrations/audit-zendesk-data.md)
   - Datenbankintegrationen {#integration}
      - [Verbinden [!DNL Amazon RDS]](data-analyst/importing-data/integrations/amazon-rds.md)
      - [Datenbanken über VPN verbinden](data-analyst/importing-data/integrations/databases-via-a-vpn.md)
      - [Verbinden Sie Ihre [!DNL MySQL Database] mit [!DNL Commerce Intelligence]](data-analyst/importing-data/integrations/db-to-mbi.md)
      - [Verbinden von Adobe Commerce](data-analyst/importing-data/integrations/magento.md)
      - [Erwartete Commerce-Daten](data-analyst/importing-data/integrations/magento-data.md)
      - [Verbinden [!DNL Microsoft SQL Server]](data-analyst/importing-data/integrations/microsoft-sql-server.md)
      - [Verbinden [!DNL MongoDB] über [!DNL SSH Tunnel]](data-analyst/importing-data/integrations/mongodb-via-ssh-tunnel.md)
      - [Verbindung [!DNL MySQL] über a [!DNL direct connection]](data-analyst/importing-data/integrations/mysql-via-a-direct-connection.md)
      - [Verbinden [!DNL MySQL] über [!DNL cPanel]](data-analyst/importing-data/integrations/mysql-via-cpanel.md)
      - [Verbinden [!DNL MySQL] über [!DNL SSH Tunnel]](data-analyst/importing-data/integrations/mysql-via-ssh-tunnel.md)
      - [Verbinden [!DNL PostgreSQ]](data-analyst/importing-data/integrations/postgresql.md)
   - Analysieren von Kampagnen {#campaigns}
      - [Analyse des Couponcodes (Basisversion)](data-analyst/analysis/ess-coupon-code-analysis.md)
      - [Analyse des Couponcodes (erweitert)](data-analyst/analysis/coupon-code-analysis.md)
      - [Schwelle für kostenlosen Versand](data-analyst/analysis/free-ship-thresh.md)
      - [Auswirkungen des Gutscheins analysieren](data-analyst/analysis/coupon-impact.md)
      - [Nutzung von Gutscheinen analysieren](data-analyst/analysis/coupon-usage.md)
      - [Steigerung des ROI bei Werbekampagnen](data-analyst/analysis/roi-ad-camp.md)
      - [Marketing-ROI](data-analyst/analysis/marketing-roi.md)
   - Kunden analysieren {#customers}
      - [Commerce-Abwanderungsraten berechnen](data-analyst/analysis/commerce-churn.md)
      - [Bestimmung der Kundenkonzentration](data-analyst/analysis/define-cust-concent.md)
      - [Definieren der Kundenabwanderung](data-analyst/analysis/define-cust-churn.md)
      - [[!DNL Expected Lifetime Value (LTV)] Analyse (Basisversion)](data-analyst/analysis/ess-expected-ltv.md)
      - [[!DNL Expected Lifetime Value (LTV)] Analyse (erweitert)](data-analyst/analysis/expected-customer-ltv.md)
      - [Tracking von Benutzerakquise Source-Daten - Überblick](data-analyst/analysis/google-track-user-acq.md)
      - [Tracking von Benutzergeräten und Browserdaten in Ihrer Datenbank](data-analyst/analysis/track-usr-dev-browser.md)
      - [Analysieren des Kaufverhaltens von Kunden](data-analyst/analysis/repurchase-behavior.md)
      - [Analyse der Website-Aktivität und der Kundenkonversionsraten](data-analyst/analysis/web-act-cust-conversion.md)
      - [Neuigkeits-, Häufigkeits- und Geldanalyse](data-analyst/analysis/rfm-analysis.md)
   - Analysieren der Geschäftsleistung {#performance}
      - [Ziele mit tatsächlichen Metriken verfolgen](data-analyst/analysis/track-goals-against-metrics.md)
      - [Analyse zurückgegebener Bestellungen](data-analyst/analysis/returned-order-analysis.md)
      - [Jahres-, Monatsvergleich, Wochenvergleich](data-analyst/analysis/year-month-week.md)
      - [Analysieren der Leistung in der Weihnachtszeit](data-analyst/analysis/holiday-season-perf.md)
      - [Analysieren des Rückgangs und der Abwanderung von Wiederholungswahrscheinlichkeiten](data-analyst/analysis/repeat-decay-churn.md)
      - [Grundlegende Analysen verstehen und erstellen](data-analyst/analysis/basic-analytics.md)
      - [Identifizieren Ihrer wertvollsten Marketing-Quellen und -Kanäle](data-analyst/analysis/most-value-source-channel.md)
      - [Grundlegendes zur UTM-Attribution [!DNL Google Analytics] ](data-analyst/analysis/utm-attributes.md)
      - [Analyse der Lagerbestände](data-analyst/analysis/analyze-inventory-level.md)
      - [Einzelhandelskalender melden](data-analyst/analysis/report-retail-calendar.md)
   - Prognosen {#forecasting}
      - [Einführung](data-analyst/analysis/forecasting.md)
- Erstellen von Berichten und Freigeben von Daten {#build}
   - [Datenbenutzer](../mbi/data-user.md)
   - Berichte {#reports}
      - [Berichtgrundlagen](data-user/reports/rpt-fundamentals.md)
      - [Welchen Report Builder sollte ich verwenden?](data-user/reports/report-builder-options.md)
      - [[!DNL Visual Report Builder]](data-user/reports/ess-rpt-build-visual.md)
      - [Visualisierungsoptionen](data-user/reports/visual-options.md)
      - [[!DNL Visual Report Builder] Filter](data-user/reports/ess-rpt-build-filters.md)
      - [[!DNL Visual Report Builder] Formeln](data-user/reports/ess-rpt-build-formulas.md)
      - [Daten verwalten](data-user/reports/ess-manage-data.md)
      - [Metriken](data-user/reports/ess-manage-data-metrics.md)
      - [Filtersätze](data-user/reports/ess-manage-data-filters.md)
      - [Bericht kopieren](data-user/reports/copy-report.md)
      - [Diagrammanalyse](data-user/reports/what-is-chart-analyzing.md)
   - Dashboards {#dashboards}
      - [Erstellen von Dashboards](data-user/dashboards/ess-dashboards.md)
      - [Vordefinierte Dashboards](data-user/dashboards/ootb-dashboards.md)
      - [Dashboard Pro](data-user/dashboards/dashboards-pro.md)
      - [Grafiken von einem anderen Benutzer importieren](data-user/dashboards/import-charts-other-user.md)
      - [Dauerhaftes Löschen eines Diagramms](data-user/dashboards/delete-chart.md)
      - [Verwenden von Dashboard-Gruppen](data-user/dashboards/using-dashboard-groups.md)
      - [Verwalten von Dashboards](data-user/dashboards/managing-dashboard.md)
      - [Löschen von Dashboards](data-user/dashboards/deleting-dashboard.md)
      - [Umbenennen von Dashboards](data-user/dashboards/renaming-dashboard.md)
      - [Standard-Dashboard einrichten](data-user/dashboards/set-default-dashboard.md)
      - [Hinzufügen von Diagrammen zu Dashboards](data-user/dashboards/add-charts-dashboard.md)
      - [Entfernen von Diagrammen aus Dashboards](data-user/dashboards/remove-charts-dashboard.md)
      - [Größe und Anordnung von Diagrammen in einem Dashboard](data-user/dashboards/resize-charts-dashboard.md)
      - [Grafiken zur Massenbearbeitung in Dashboards](data-user/dashboards/bulk-edit-dashboard.md)
      - [Klonen von Dashboards](data-user/dashboards/clone-dashboard.md)
      - [Suchen nach Dashboards](data-user/dashboards/search-dashboard.md)
      - [Freigeben von Dashboards für andere Benutzer](data-user/dashboards/share-dashboard-with-users.md)
      - [Organisationsweites Freigeben von Dashboards](data-user/dashboards/share-dashboard-with-org.md)
      - [Zugreifen auf freigegebene Dashboards](data-user/dashboards/access-shared-dashboard.md)
      - [Zugriff auf freigegebene Dashboards ändern](data-user/dashboards/change-access-dashboard.md)
      - [Verlassen (Freigabe aufheben) eines Dashboards](data-user/dashboards/leave-dashboard.md)
   - Freigeben von Daten {#share}
      - [Daten freigeben](data-user/export-data/share-data.md)
      - [Exportieren von Diagrammdaten](data-user/export-data/exp-chart-dash.md)
      - [Automatisierte E-Mail-Zusammenfassungen](data-user/export-data/email-summaries.md)
- Best Practices {#best-practices}
   - Arbeiten mit Daten {#data}
      - [Daten verwenden](best-practices/work-data.md)
      - [UTM-Tagging in [!DNL Google Analytics]](best-practices/utm-tagging-google.md)
      - [Formatieren und Importieren von Finanzdaten](best-practices/format-import-financial-data.md)
      - [Empfohlene Daten-Dimensionen für Segmentierung und Filterung](best-practices/segment-filter.md)
      - [Überprüfen des Aktualisierungszyklusstatus](best-practices/check-update-cycle.md)
      - [Verringern der Aktualisierungszyklusdauer](best-practices/reduce-update-cycle-time.md)
      - [Ändern der Datenbank zur Unterstützung der inkrementellen Replikation](best-practices/mod-db-inc-replication.md)
      - [Datenbank für Analysen optimieren](best-practices/opt-db-analysis.md)
      - [Optimieren Ihrer [!DNL SQL] Abfragen](best-practices/optimizing-your-sql-queries.md)
      - [Grundlegendes zur [!DNL Commerce Intelligence] Umgebung](best-practices/understanding-magento.md)
   - Projektorganisation {#project}
      - [Benennen von Berichten und Elementen in [!DNL Commerce Intelligence]](best-practices/naming-elements.md)
      - [Tabellen konsolidieren](best-practices/consolidating-your-tables.md)
      - [Entschlüsseln Ihres [!DNL Commerce Intelligence] Kontos](best-practices/declutter-account.md)
   - Arbeiten mit Dashboards {#working-dashboards}
      - [Freigeben von Dashboards](best-practices/share-dashboard-best-practice.md)
      - [Erstellen eines Anleger-Dashboards](best-practices/build-investor-dashboard.md)
- Tutorials {#tutorials}
   - [Verwenden des  [!DNL Visual Report Builder]](tutorials/using-visual-report-builder.md)
   - [Verwenden der Zeitoptionen im  [!DNL Visual Report Builder]](tutorials/time-options-visual-rpt-bldr.md)
   - [Erstellen von Visualisierungen für eine [!DNL SQL] Abfrage](tutorials/create-visuals-from-sql.md)
   - [Rohdaten exportieren](tutorials/export-raw-data.md)
