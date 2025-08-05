Skip to content
Navigation Menu
wmig999-lab
--main-menu

Type / to search
Code
Issues
Pull requests
Actions
Projects
Wiki
Security
Insights
Settings
Files
Go to file
t
README.md
index 3.html
--main-menu
/index 3.html
wmig999-lab
wmig999-lab
Update index 3.html
c2bd6f6
 · 
17 minutes ago
--main-menu
/index 3.html

Code

Blame
3478 lines (3432 loc) · 160 KB
      <!DOCTYPE html>
<html lang="ru">
   <head>
      <meta charset="UTF-8">
      <meta name="viewport" content="width=device-width, initial-scale=1.0">
      <title>ХабЗа - Цифровой строительный портал</title>
      <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.min.css" rel="stylesheet">
      <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap-icons@1.11.0/font/bootstrap-icons.css">
      <style>
         :root {
         --primary-color: #1e3a5f;
         --secondary-color: #f8a533;
         --accent-color: #2c7a7b;
         --light-bg: #f8f9fa;
         --dark-text: #333;
         --success-color: #28a745;
         --danger-color: #dc3545;
         --warning-color: #ffc107;
         --info-color: #17a2b8;
         }
         body {
         font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
         color: var(--dark-text);
         }
         /* Навигация */
         .navbar {
         background-color: white;
         box-shadow: 0 2px 10px rgba(0,0,0,0.1);
         }
         .navbar-brand {
         font-weight: 700;
         font-size: 1.5rem;
         color: var(--primary-color) !important;
         }
         .nav-link {
         color: var(--dark-text) !important;
         font-weight: 500;
         margin: 0 5px;
         transition: all 0.3s ease;
         }
         .nav-link:hover {
         color: var(--accent-color) !important;
         }
         .nav-link.active {
         color: var(--accent-color) !important;
         font-weight: 600;
         }
         /* Главная секция */
         .hero-section {
         background: linear-gradient(135deg, var(--primary-color) 0%, var(--accent-color) 100%);
         color: white;
         padding: 100px 0;
         position: relative;
         overflow: hidden;
         }
         .hero-section::before {
         content: "";
         position: absolute;
         top: 0;
         right: 0;
         width: 50%;
         height: 100%;
         background: url('https://images.unsplash.com/photo-1512917774080-9991f1c4c750?ixlib=rb-4.0.3&auto=format&fit=crop&w=1950&q=80') no-repeat center center;
         background-size: cover;
         opacity: 0.15;
         }
         .hero-content {
         position: relative;
         z-index: 2;
         }
         .section-title {
         font-weight: 700;
         margin-bottom: 40px;
         position: relative;
         padding-bottom: 15px;
         }
         .section-title::after {
         content: "";
         position: absolute;
         bottom: 0;
         left: 0;
         width: 60px;
         height: 4px;
         background-color: var(--secondary-color);
         }
         .btn-primary-custom {
         background-color: var(--secondary-color);
         border: none;
         color: white;
         font-weight: 600;
         padding: 12px 30px;
         border-radius: 50px;
         transition: all 0.3s ease;
         }
         .btn-primary-custom:hover {
         background-color: #e6951f;
         transform: translateY(-3px);
         box-shadow: 0 10px 20px rgba(248, 165, 51, 0.3);
         }
         .btn-outline-custom {
         border: 2px solid var(--secondary-color);
         color: var(--secondary-color);
         font-weight: 600;
         padding: 10px 28px;
         border-radius: 50px;
         transition: all 0.3s ease;
         }
         .btn-outline-custom:hover {
         background-color: var(--secondary-color);
         color: white;
         transform: translateY(-3px);
         }
         /* Возможности */
         .feature-card {
         background: white;
         border-radius: 15px;
         padding: 30px;
         height: 100%;
         box-shadow: 0 10px 30px rgba(0, 0, 0, 0.05);
         transition: all 0.3s ease;
         border-left: 4px solid var(--accent-color);
         }
         .feature-card:hover {
         transform: translateY(-10px);
         box-shadow: 0 15px 40px rgba(0, 0, 0, 0.1);
         }
         .feature-icon {
         font-size: 3rem;
         color: var(--accent-color);
         margin-bottom: 20px;
         }
         /* Аналитика проектной документации */
         .analytics-section {
         background-color: var(--light-bg);
         padding: 80px 0;
         }
         .analytics-card {
         background: white;
         border-radius: 15px;
         padding: 30px;
         box-shadow: 0 10px 30px rgba(0, 0, 0, 0.05);
         margin-bottom: 30px;
         }
         .upload-area {
         border: 2px dashed var(--accent-color);
         border-radius: 15px;
         padding: 60px 30px;
         text-align: center;
         background-color: rgba(44, 122, 123, 0.05);
         transition: all 0.3s ease;
         cursor: pointer;
         }
         .upload-area:hover {
         background-color: rgba(44, 122, 123, 0.1);
         border-color: var(--secondary-color);
         }
         .upload-icon {
         font-size: 4rem;
         color: var(--accent-color);
         margin-bottom: 20px;
         }
         .analysis-progress {
         display: none;
         margin-top: 30px;
         }
         .progress {
         height: 10px;
         border-radius: 10px;
         overflow: hidden;
         background-color: #e9ecef;
         }
         .progress-bar {
         background: linear-gradient(90deg, var(--accent-color), var(--secondary-color));
         transition: width 0.6s ease;
         }
         .analysis-steps {
         margin-top: 20px;
         }
         .step {
         display: flex;
         align-items: center;
         margin-bottom: 15px;
         opacity: 0.5;
         transition: all 0.3s ease;
         }
         .step.active {
         opacity: 1;
         }
         .step-icon {
         width: 40px;
         height: 40px;
         border-radius: 50%;
         background-color: var(--light-bg);
         display: flex;
         align-items: center;
         justify-content: center;
         margin-right: 15px;
         font-weight: 700;
         color: var(--primary-color);
         }
         .step.active .step-icon {
         background-color: var(--accent-color);
         color: white;
         }
         .step.completed .step-icon {
         background-color: var(--success-color);
         color: white;
         }
         .results-section {
         display: none;
         margin-top: 40px;
         }
         .cost-summary {
         background: linear-gradient(135deg, var(--primary-color), var(--accent-color));
         color: white;
         border-radius: 15px;
         padding: 30px;
         margin-bottom: 30px;
         }
         .cost-item {
         display: flex;
         justify-content: space-between;
         align-items: center;
         padding: 15px 0;
         border-bottom: 1px solid rgba(255, 255, 255, 0.2);
         }
         .cost-item:last-child {
         border-bottom: none;
         font-size: 1.2rem;
         font-weight: 700;
         }
         .cost-value {
         font-size: 1.5rem;
         font-weight: 700;
         }
         .cost-deviation {
         font-size: 0.9rem;
         padding: 5px 10px;
         border-radius: 50px;
         margin-left: 10px;
         }
         .deviation-up {
         background-color: rgba(220, 53, 69, 0.2);
         color: var(--danger-color);
         }
         .deviation-down {
         background-color: rgba(40, 167, 69, 0.2);
         color: var(--success-color);
         }
         .materials-table {
         background: white;
         border-radius: 15px;
         overflow: hidden;
         box-shadow: 0 5px 20px rgba(0, 0, 0, 0.05);
         }
         .table thead {
         background-color: var(--primary-color);
         color: white;
         }
         .table tbody tr {
         transition: all 0.3s ease;
         }
         .table tbody tr:hover {
         background-color: var(--light-bg);
         }
         .price-trend {
         font-size: 0.9rem;
         font-weight: 600;
         }
         .trend-up {
         color: var(--danger-color);
         }
         .trend-down {
         color: var(--success-color);
         }
         .supplier-card {
         background: white;
         border-radius: 15px;
         padding: 25px;
         box-shadow: 0 5px 20px rgba(0, 0, 0, 0.05);
         margin-bottom: 20px;
         transition: all 0.3s ease;
         border-left: 4px solid var(--accent-color);
         }
         .supplier-card:hover {
         transform: translateY(-5px);
         box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
         }
         .supplier-header {
         display: flex;
         justify-content: space-between;
         align-items: start;
         margin-bottom: 15px;
         }
         .supplier-name {
         font-weight: 700;
         font-size: 1.1rem;
         color: var(--primary-color);
         }
         .supplier-rating {
         display: flex;
         align-items: center;
         color: var(--secondary-color);
         }
         .supplier-details {
         display: grid;
         grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
         gap: 15px;
         margin-bottom: 20px;
         }
         .detail-item {
         display: flex;
         align-items: center;
         }
         .detail-icon {
         color: var(--accent-color);
         margin-right: 10px;
         }
         .supplier-actions {
         display: flex;
         gap: 10px;
         }
         .btn-request {
         background-color: var(--secondary-color);
         border: none;
         color: white;
         font-weight: 600;
         padding: 10px 20px;
         border-radius: 50px;
         transition: all 0.3s ease;
         }
         .btn-request:hover {
         background-color: #e6951f;
         transform: translateY(-3px);
         }
         .btn-contact {
         background-color: transparent;
         border: 2px solid var(--accent-color);
         color: var(--accent-color);
         font-weight: 600;
         padding: 8px 18px;
         border-radius: 50px;
         transition: all 0.3s ease;
         }
         .btn-contact:hover {
         background-color: var(--accent-color);
         color: white;
         }
         .ai-badge {
         background: linear-gradient(135deg, var(--secondary-color), var(--accent-color));
         color: white;
         padding: 5px 15px;
         border-radius: 50px;
         font-size: 0.8rem;
         font-weight: 700;
         display: inline-flex;
         align-items: center;
         margin-left: 10px;
         }
         .ai-badge i {
         margin-right: 5px;
         }
         .notification-badge {
         position: absolute;
         top: -5px;
         right: -5px;
         background-color: var(--danger-color);
         color: white;
         border-radius: 50%;
         width: 20px;
         height: 20px;
         display: flex;
         align-items: center;
         justify-content: center;
         font-size: 0.8rem;
         font-weight: 700;
         }
         /* Модуль поиска поставщиков */
         .supplier-search-section {
         background-color: var(--light-bg);
         padding: 80px 0;
         }
         .search-filters {
         background: white;
         border-radius: 15px;
         padding: 30px;
         box-shadow: 0 10px 30px rgba(0, 0, 0, 0.05);
         margin-bottom: 30px;
         }
         .filter-group {
         margin-bottom: 20px;
         }
         .filter-label {
         font-weight: 600;
         color: var(--primary-color);
         margin-bottom: 10px;
         display: flex;
         align-items: center;
         }
         .filter-label i {
         margin-right: 8px;
         color: var(--accent-color);
         }
         .optimization-options {
         display: flex;
         gap: 15px;
         margin-top: 20px;
         flex-wrap: wrap;
         }
         .optimization-card {
         background: white;
         border: 2px solid #e9ecef;
         border-radius: 15px;
         padding: 20px;
         text-align: center;
         cursor: pointer;
         transition: all 0.3s ease;
         flex: 1;
         min-width: 200px;
         }
         .optimization-card:hover {
         border-color: var(--accent-color);
         transform: translateY(-5px);
         box-shadow: 0 10px 20px rgba(0, 0, 0, 0.1);
         }
         .optimization-card.selected {
         border-color: var(--secondary-color);
         background-color: rgba(248, 165, 51, 0.1);
         }
         .optimization-icon {
         font-size: 2.5rem;
         color: var(--accent-color);
         margin-bottom: 15px;
         }
         .optimization-title {
         font-weight: 700;
         margin-bottom: 10px;
         }
         .optimization-desc {
         font-size: 0.9rem;
         color: #666;
         }
         .search-results {
         display: none;
         }
         .result-header {
         background: linear-gradient(135deg, var(--primary-color), var(--accent-color));
         color: white;
         border-radius: 15px;
         padding: 30px;
         margin-bottom: 30px;
         }
         .result-summary {
         display: grid;
         grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
         gap: 20px;
         margin-top: 20px;
         }
         .summary-item {
         text-align: center;
         }
         .summary-value {
         font-size: 2rem;
         font-weight: 700;
         margin-bottom: 5px;
         }
         .summary-label {
         font-size: 0.9rem;
         opacity: 0.9;
         }
         .supplier-match-card {
         background: white;
         border-radius: 15px;
         padding: 25px;
         box-shadow: 0 5px 20px rgba(0, 0, 0, 0.05);
         margin-bottom: 20px;
         transition: all 0.3s ease;
         position: relative;
         overflow: hidden;
         }
         .supplier-match-card::before {
         content: "";
         position: absolute;
         top: 0;
         left: 0;
         width: 5px;
         height: 100%;
         background-color: var(--success-color);
         }
         .supplier-match-card.risk-high::before {
         background-color: var(--danger-color);
         }
         .supplier-match-card.risk-medium::before {
         background-color: var(--warning-color);
         }
         .supplier-match-card:hover {
         transform: translateY(-5px);
         box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
         }
         .match-header {
         display: flex;
         justify-content: space-between;
         align-items: start;
         margin-bottom: 20px;
         }
         .match-score {
         background: var(--success-color);
         color: white;
         padding: 8px 15px;
         border-radius: 50px;
         font-weight: 700;
         font-size: 0.9rem;
         }
         .match-score.medium {
         background: var(--warning-color);
         }
         .match-score.low {
         background: var(--danger-color);
         }
         .match-details {
         display: grid;
         grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
         gap: 15px;
         margin-bottom: 20px;
         }
         .match-detail {
         display: flex;
         flex-direction: column;
         }
         .detail-label {
         font-size: 0.8rem;
         color: #666;
         margin-bottom: 3px;
         }
         .detail-value {
         font-weight: 600;
         color: var(--primary-color);
         }
         .risk-alert {
         background-color: rgba(220, 53, 69, 0.1);
         border-left: 4px solid var(--danger-color);
         padding: 15px;
         border-radius: 8px;
         margin-bottom: 15px;
         display: flex;
         align-items: center;
         }
         .risk-alert.medium {
         background-color: rgba(255, 193, 7, 0.1);
         border-left-color: var(--warning-color);
         }
         .risk-alert i {
         font-size: 1.5rem;
         margin-right: 15px;
         color: var(--danger-color);
         }
         .risk-alert.medium i {
         color: var(--warning-color);
         }
         .match-actions {
         display: flex;
         gap: 10px;
         flex-wrap: wrap;
         }
         .comparison-table {
         background: white;
         border-radius: 15px;
         overflow: hidden;
         box-shadow: 0 5px 20px rgba(0, 0, 0, 0.05);
         margin-top: 30px;
         }
         .price-cell {
         font-weight: 700;
         color: var(--success-color);
         }
         .time-cell {
         font-weight: 600;
         }
         .rating-cell {
         color: var(--secondary-color);
         }
         .notification-panel {
         position: fixed;
         top: 80px;
         right: 20px;
         width: 350px;
         max-height: 500px;
         background: white;
         border-radius: 15px;
         box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);
         z-index: 1000;
         display: none;
         overflow: hidden;
         }
         .notification-header {
         background: var(--primary-color);
         color: white;
         padding: 20px;
         display: flex;
         justify-content: space-between;
         align-items: center;
         }
         .notification-list {
         max-height: 400px;
         overflow-y: auto;
         padding: 20px;
         }
         .notification-item {
         padding: 15px;
         border-radius: 10px;
         margin-bottom: 15px;
         background: var(--light-bg);
         border-left: 4px solid var(--warning-color);
         }
         .notification-item.high-risk {
         border-left-color: var(--danger-color);
         background: rgba(220, 53, 69, 0.1);
         }
         .notification-item.success {
         border-left-color: var(--success-color);
         background: rgba(40, 167, 69, 0.1);
         }
         .notification-time {
         font-size: 0.8rem;
         color: #666;
         margin-top: 5px;
         }
         .map-container {
         height: 300px;
         background-color: var(--light-bg);
         border-radius: 15px;
         margin-top: 20px;
         position: relative;
         overflow: hidden;
         }
         .map-placeholder {
         position: absolute;
         top: 50%;
         left: 50%;
         transform: translate(-50%, -50%);
         text-align: center;
         color: #666;
         }
         .map-placeholder i {
         font-size: 3rem;
         color: #ccc;
         margin-bottom: 10px;
         }
         /* Градостроительный Ассистент */
         .urban-assistant-section {
         background-color: var(--light-bg);
         padding: 80px 0;
         }
         .assistant-card {
         background: white;
         border-radius: 15px;
         padding: 30px;
         box-shadow: 0 10px 30px rgba(0, 0, 0, 0.05);
         }
         .assistant-header {
         text-align: center;
         margin-bottom: 30px;
         }
         .assistant-header h3 {
         color: var(--primary-color);
         margin-bottom: 10px;
         }
         .map-selector {
         margin-top: 20px;
         border-radius: 15px;
         overflow: hidden;
         }
         .assistant-results {
         margin-top: 30px;
         }
         .plot-map {
         height: 300px;
         background-color: var(--light-bg);
         border-radius: 15px;
         margin-bottom: 30px;
         overflow: hidden;
         }
         .plot-parameters {
         margin-bottom: 30px;
         }
         .plot-parameters h4 {
         color: var(--primary-color);
         margin-bottom: 20px;
         }
         .potential-metrics {
         margin-top: 30px;
         }
         .potential-metrics h4 {
         color: var(--primary-color);
         margin-bottom: 20px;
         }
         .metric-card {
         background: var(--light-bg);
         border-radius: 15px;
         padding: 20px;
         text-align: center;
         height: 100%;
         }
         .metric-value {
         font-size: 1.8rem;
         font-weight: 700;
         color: var(--secondary-color);
         margin-bottom: 5px;
         }
         .metric-label {
         font-size: 0.9rem;
         color: #666;
         }
         .restrictions-list {
         margin-top: 20px;
         }
         .restriction-item {
         background: white;
         border-radius: 15px;
         padding: 20px;
         margin-bottom: 20px;
         box-shadow: 0 5px 15px rgba(0, 0, 0, 0.05);
         border-left: 4px solid var(--warning-color);
         }
         .restriction-item.high-risk {
         border-left-color: var(--danger-color);
         }
         .restriction-item.low-risk {
         border-left-color: var(--success-color);
         }
         .restriction-header {
         display: flex;
         justify-content: space-between;
         align-items: center;
         margin-bottom: 15px;
         }
         .restriction-title {
         font-weight: 600;
         color: var(--primary-color);
         }
         .restriction-badge {
         padding: 5px 15px;
         border-radius: 50px;
         font-size: 0.8rem;
         font-weight: 600;
         color: white;
         }
         .restriction-item.high-risk .restriction-badge {
         background-color: var(--danger-color);
         }
         .restriction-item.medium-risk .restriction-badge {
         background-color: var(--warning-color);
         }
         .restriction-item.low-risk .restriction-badge {
         background-color: var(--success-color);
         }
         .restriction-solution {
         margin-top: 15px;
         padding-top: 15px;
         border-top: 1px dashed #eee;
         }
         .geology-risks {
         margin-top: 30px;
         }
         .geology-risks h5 {
         color: var(--primary-color);
         margin-bottom: 15px;
         }
         .risk-indicator {
         margin-bottom: 20px;
         }
         .risk-title {
         font-weight: 600;
         margin-bottom: 5px;
         }
         .risk-bar {
         height: 10px;
         background-color: #eee;
         border-radius: 5px;
         overflow: hidden;
         margin-bottom: 5px;
         }
         .risk-progress {
         height: 100%;
         border-radius: 5px;
         }
         .risk-value {
         font-weight: 600;
         color: var(--primary-color);
         }
         .infrastructure-map {
         height: 300px;
         background-color: var(--light-bg);
         border-radius: 15px;
         margin-bottom: 30px;
         overflow: hidden;
         }
         .infrastructure-metrics {
         margin-bottom: 30px;
         }
         .infrastructure-metrics h5 {
         color: var(--primary-color);
         margin-bottom: 15px;
         }
         .social-infrastructure {
         margin-top: 30px;
         }
         .social-infrastructure h5 {
         color: var(--primary-color);
         margin-bottom: 20px;
         }
         .infra-item {
         background: var(--light-bg);
         border-radius: 15px;
         padding: 20px;
         text-align: center;
         height: 100%;
         }
         .infra-item i {
         font-size: 2rem;
         color: var(--accent-color);
         margin-bottom: 10px;
         }
         .infra-name {
         font-weight: 600;
         margin-bottom: 5px;
         }
         .infra-distance {
         color: #666;
         }
         .vri-comparison {
         margin-bottom: 30px;
         }
         .vri-comparison h5 {
         color: var(--primary-color);
         margin-bottom: 15px;
         }
         .development-recommendations {
         margin-bottom: 30px;
         }
         .development-recommendations h5 {
         color: var(--primary-color);
         margin-bottom: 20px;
         }
         .recommendation-card {
         background: var(--light-bg);
         border-radius: 15px;
         padding: 25px;
         margin-bottom: 20px;
         }
         .recommendation-header {
         display: flex;
         justify-content: space-between;
         align-items: center;
         margin-bottom: 15px;
         }
         .recommendation-title {
         font-weight: 600;
         color: var(--primary-color);
         }
         .recommendation-score {
         background: linear-gradient(135deg, var(--secondary-color), var(--accent-color));
         color: white;
         padding: 5px 15px;
         border-radius: 50px;
         font-weight: 700;
         }
         .recommendation-steps {
         background: white;
         border-radius: 15px;
         padding: 20px;
         box-shadow: 0 5px 15px rgba(0, 0, 0, 0.05);
         }
         .recommendation-steps h6 {
         color: var(--primary-color);
         margin-bottom: 15px;
         }
         .recommendation-steps ol {
         padding-left: 20px;
         }
         .recommendation-steps li {
         margin-bottom: 10px;
         }
         .action-buttons {
         display: flex;
         flex-wrap: wrap;
         gap: 15px;
         justify-content: center;
         }
         /* Интеграция с 1С */
         .integration-section {
         background-color: var(--light-bg);
         padding: 80px 0;
         }
         .integration-card {
         background: white;
         border-radius: 15px;
         padding: 30px;
         height: 100%;
         box-shadow: 0 5px 20px rgba(0, 0, 0, 0.05);
         transition: all 0.3s ease;
         position: relative;
         overflow: hidden;
         }
         .integration-card::before {
         content: "";
         position: absolute;
         top: 0;
         left: 0;
         width: 5px;
         height: 100%;
         background-color: var(--secondary-color);
         }
         .integration-card:hover {
         transform: translateY(-5px);
         box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
         }
         .integration-level {
         font-weight: 700;
         color: var(--primary-color);
         margin-bottom: 15px;
         }
         /* Поиск товаров */
         .search-section {
         background-color: var(--light-bg);
         padding: 80px 0;
         }
         .search-container {
         background: white;
         border-radius: 15px;
         padding: 40px;
         box-shadow: 0 10px 30px rgba(0, 0, 0, 0.05);
         }
         .search-form {
         display: flex;
         flex-wrap: wrap;
         gap: 15px;
         margin-bottom: 30px;
         }
         .search-input {
         flex: 1;
         min-width: 250px;
         padding: 15px 20px;
         border: 1px solid #ddd;
         border-radius: 50px;
         font-size: 1rem;
         }
         .search-btn {
         background-color: var(--secondary-color);
         border: none;
         color: white;
         font-weight: 600;
         padding: 15px 30px;
         border-radius: 50px;
         cursor: pointer;
         transition: all 0.3s ease;
         }
         .search-btn:hover {
         background-color: #e6951f;
         }
         .filter-tags {
         display: flex;
         flex-wrap: wrap;
         gap: 10px;
         margin-bottom: 20px;
         }
         .filter-tag {
         background-color: var(--light-bg);
         border: 1px solid #ddd;
         border-radius: 50px;
         padding: 8px 15px;
         font-size: 0.9rem;
         cursor: pointer;
         transition: all 0.3s ease;
         }
         .filter-tag:hover, .filter-tag.active {
         background-color: var(--accent-color);
         color: white;
         border-color: var(--accent-color);
         }
         .product-card {
         background: white;
         border-radius: 15px;
         overflow: hidden;
         box-shadow: 0 5px 20px rgba(0, 0, 0, 0.05);
         transition: all 0.3s ease;
         height: 100%;
         }
         .product-card:hover {
         transform: translateY(-10px);
         box-shadow: 0 15px 40px rgba(0, 0, 0, 0.1);
         }
         .product-img {
         height: 200px;
         background-color: var(--light-bg);
         display: flex;
         align-items: center;
         justify-content: center;
         font-size: 3rem;
         color: #ccc;
         }
         .product-info {
         padding: 20px;
         }
         .product-title {
         font-weight: 600;
         margin-bottom: 10px;
         font-size: 1.1rem;
         }
         .product-meta {
         display: flex;
         justify-content: space-between;
         margin-bottom: 15px;
         font-size: 0.9rem;
         color: #666;
         }
         .product-price {
         font-size: 1.3rem;
         font-weight: 700;
         color: var(--primary-color);
         margin-bottom: 15px;
         }
         .product-supplier {
         font-size: 0.9rem;
         color: #666;
         margin-bottom: 15px;
         }
         .add-to-cart {
         width: 100%;
         background-color: var(--secondary-color);
         border: none;
         color: white;
         font-weight: 600;
         padding: 12px;
         border-radius: 50px;
         cursor: pointer;
         transition: all 0.3s ease;
         }
         .add-to-cart:hover {
         background-color: #e6951f;
         }
         /* Личный кабинет */
         .dashboard-section {
         padding: 80px 0;
         }
         .dashboard-card {
         background: white;
         border-radius: 15px;
         padding: 30px;
         box-shadow: 0 10px 30px rgba(0, 0, 0, 0.05);
         height: 100%;
         }
         .dashboard-header {
         display: flex;
         justify-content: space-between;
         align-items: center;
         margin-bottom: 30px;
         }
         .dashboard-title {
         font-weight: 700;
         color: var(--primary-color);
         }
         .dashboard-tabs {
         display: flex;
         border-bottom: 1px solid #eee;
         margin-bottom: 30px;
         }
         .dashboard-tab {
         padding: 15px 25px;
         font-weight: 600;
         color: #666;
         cursor: pointer;
         border-bottom: 3px solid transparent;
         transition: all 0.3s ease;
         position: relative;
         }
         .dashboard-tab.active {
         color: var(--primary-color);
         border-bottom-color: var(--secondary-color);
         }
         .order-item {
         display: flex;
         justify-content: space-between;
         align-items: center;
         padding: 15px 0;
         border-bottom: 1px dashed #eee;
         }
         .order-item:last-child {
         border-bottom: none;
         }
         .order-id {
         font-weight: 600;
         }
         .order-status {
         padding: 5px 15px;
         border-radius: 50px;
         font-size: 0.8rem;
         font-weight: 600;
         }
         .status-new {
         background-color: rgba(248, 165, 51, 0.2);
         color: var(--secondary-color);
         }
         .status-processing {
         background-color: rgba(44, 122, 123, 0.2);
         color: var(--accent-color);
         }
         .status-completed {
         background-color: rgba(40, 167, 69, 0.2);
         color: #28a745;
         }
         .integration-status {
         display: flex;
         align-items: center;
         margin-bottom: 20px;
         }
         .status-indicator {
         width: 15px;
         height: 15px;
         border-radius: 50%;
         margin-right: 10px;
         }
         .status-active {
         background-color: #28a745;
         }
         .status-inactive {
         background-color: #dc3545;
         }
         .integration-actions {
         display: flex;
         gap: 10px;
         margin-top: 20px;
         }
         .btn-small {
         padding: 8px 15px;
         font-size: 0.9rem;
         }
         /* Тарифы */
         .pricing-card {
         background: white;
         border-radius: 15px;
         padding: 40px 30px;
         box-shadow: 0 10px 30px rgba(0, 0, 0, 0.05);
         height: 100%;
         transition: all 0.3s ease;
         position: relative;
         overflow: hidden;
         }
         .pricing-card.popular {
         border: 2px solid var(--secondary-color);
         }
         .pricing-card.popular::before {
         content: "Популярный";
         position: absolute;
         top: 15px;
         right: -30px;
         background-color: var(--secondary-color);
         color: white;
         padding: 5px 40px;
         transform: rotate(45deg);
         font-size: 0.8rem;
         font-weight: 700;
         }
         .pricing-card:hover {
         transform: translateY(-10px);
         box-shadow: 0 15px 40px rgba(0, 0, 0, 0.1);
         }
         .plan-name {
         font-size: 1.5rem;
         font-weight: 700;
         color: var(--primary-color);
         margin-bottom: 10px;
         }
         .plan-price {
         font-size: 2.5rem;
         font-weight: 700;
         color: var(--secondary-color);
         margin-bottom: 20px;
         }
         .plan-features {
         list-style: none;
         padding: 0;
         margin-bottom: 30px;
         }
         .plan-features li {
         padding: 8px 0;
         border-bottom: 1px dashed #eee;
         }
         .plan-features li:last-child {
         border-bottom: none;
         }
         .plan-features li i {
         color: var(--accent-color);
         margin-right: 10px;
         }
         /* Отзывы */
         .testimonial-card {
         background: white;
         border-radius: 15px;
         padding: 30px;
         box-shadow: 0 5px 20px rgba(0, 0, 0, 0.05);
         margin-bottom: 30px;
         }
         .testimonial-text {
         font-style: italic;
         margin-bottom: 20px;
         position: relative;
         padding-left: 25px;
         }
         .testimonial-text::before {
         content: """;
         position: absolute;
         left: 0;
         top: -10px;
         font-size: 3rem;
         color: var(--secondary-color);
         opacity: 0.5;
         }
         .client-info {
         display: flex;
         align-items: center;
         }
         .client-avatar {
         width: 60px;
         height: 60px;
         border-radius: 50%;
         background-color: var(--light-bg);
         display: flex;
         align-items: center;
         justify-content: center;
         margin-right: 15px;
         font-weight: 700;
         color: var(--primary-color);
         }
         /* Футер */
         footer {
         background-color: var(--primary-color);
         color: white;
         padding: 60px 0 30px;
         }
         .footer-logo {
         font-size: 1.8rem;
         font-weight: 700;
         margin-bottom: 20px;
         }
         .footer-links {
         list-style: none;
         padding: 0;
         }
         .footer-links li {
         margin-bottom: 10px;
         }
         .footer-links a {
         color: rgba(255, 255, 255, 0.8);
         text-decoration: none;
         transition: all 0.3s ease;
         }
         .footer-links a:hover {
         color: var(--secondary-color);
         padding-left: 5px;
         }
         .social-icons a {
         display: inline-block;
         width: 40px;
         height: 40px;
         background-color: rgba(255, 255, 255, 0.1);
         border-radius: 50%;
         text-align: center;
         line-height: 40px;
         margin-right: 10px;
         color: white;
         transition: all 0.3s ease;
         }
         .social-icons a:hover {
         background-color: var(--secondary-color);
         transform: translateY(-3px);
         }
         .copyright {
         text-align: center;
         padding-top: 30px;
         margin-top: 30px;
         border-top: 1px solid rgba(255, 255, 255, 0.1);
         font-size: 0.9rem;
         color: rgba(255, 255, 255, 0.7);
         }
         /* Модальные окна */
         .modal-content {
         border-radius: 15px;
         border: none;
         }
         .modal-header {
         background-color: var(--primary-color);
         color: white;
         border-radius: 15px 15px 0 0;
         border: none;
         }
         .modal-body {
         padding: 30px;
         }
         .file-upload {
         border: 2px dashed var(--accent-color);
         border-radius: 15px;
         padding: 40px;
         text-align: center;
         background-color: rgba(44, 122, 123, 0.05);
         margin-bottom: 20px;
         }
         .file-types {
         display: flex;
         flex-wrap: wrap;
         gap: 10px;
         justify-content: center;
         margin-top: 20px;
         }
         .file-type {
         background-color: var(--light-bg);
         border: 1px solid #ddd;
         border-radius: 50px;
         padding: 8px 15px;
         font-size: 0.9rem;
         display: flex;
         align-items: center;
         }
         .file-type i {
         margin-right: 5px;
         color: var(--accent-color);
         }
         .forecast-chart {
         height: 300px;
         background-color: var(--light-bg);
         border-radius: 15px;
         padding: 20px;
         margin-top: 20px;
         position: relative;
         overflow: hidden;
         }
         .chart-placeholder {
         position: absolute;
         top: 50%;
         left: 50%;
         transform: translate(-50%, -50%);
         text-align: center;
         color: #666;
         }
         .chart-placeholder i {
         font-size: 3rem;
         color: #ccc;
         margin-bottom: 10px;
         }
         /* Адаптивность */
         @media (max-width: 768px) {
         .hero-section {
         padding: 60px 0;
         }
         .hero-section::before {
         width: 100%;
         opacity: 0.1;
         }
         .search-form {
         flex-direction: column;
         }
         .search-input {
         min-width: 100%;
         }
         .dashboard-tabs {
         overflow-x: auto;
         white-space: nowrap;
         }
         .dashboard-tab {
         padding: 10px 15px;
         }
         .notification-panel {
         width: calc(100% - 40px);
         right: 20px;
         left: 20px;
         }
         .optimization-options {
         flex-direction: column;
         }
         .optimization-card {
         min-width: 100%;
         }
         .action-buttons {
         flex-direction: column;
         }
         .action-buttons .btn {
         width: 100%;
         }
         }
      </style>
   </head>
   <body>
      <!-- Навигация -->
      <nav class="navbar navbar-expand-lg navbar-light sticky-top">
         <div class="container">
            <a class="navbar-brand d-flex align-items-center" href="#home">
            <i class="bi bi-building" style="font-size: 1.8rem; color: var(--primary-color); margin-right: 10px;"></i>
            <span>ХабЗа</span>
            </a>
            <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav">
            <span class="navbar-toggler-icon"></span>
            </button>
            <div class="collapse navbar-collapse" id="navbarNav">
               <ul class="navbar-nav ms-auto">
                  <li class="nav-item">
                     <a class="nav-link active" href="#home">Главная</a>
                  </li>
                  <li class="nav-item">
                     <a class="nav-link" href="#features">Возможности</a>
                  </li>
                  <li class="nav-item">
                     <a class="nav-link" href="#analytics">Аналитика</a>
                  </li>
                  <li class="nav-item">
                     <a class="nav-link" href="#supplier-search">Поиск поставщиков</a>
                  </li>
                  <li class="nav-item">
                     <a class="nav-link" href="#urban-assistant">Град. ассистент</a>
                  </li>
                  <li class="nav-item">
                     <a class="nav-link" href="#integration">Интеграция</a>
                  </li>
                  <li class="nav-item">
                     <a class="nav-link" href="#pricing">Тарифы</a>
                  </li>
                  <li class="nav-item ms-3">
                     <a class="btn btn-outline-custom btn-sm" href="#" data-bs-toggle="modal" data-bs-target="#loginModal">Вход</a>
                  </li>
                  <li class="nav-item ms-2">
                     <a class="btn btn-primary-custom btn-sm" href="#" data-bs-toggle="modal" data-bs-target="#registerModal">Регистрация</a>
                  </li>
               </ul>
            </div>
         </div>
      </nav>
      <!-- Главная секция -->
      <section id="home" class="hero-section">
         <div class="container">
            <div class="row align-items-center">
               <div class="col-lg-6">
                  <div class="hero-content">
                     <h1 class="display-4 fw-bold mb-4">Цифровой строительный портал</h1>
                     <p class="lead mb-4">Прямая связь между производителями и застройщиками. Автоматизация закупок и продаж стройматериалов с интеграцией 1С.</p>
                     <div class="d-flex flex-wrap gap-3">
                        <a href="#features" class="btn btn-primary-custom btn-lg">Я покупатель</a>
                        <a href="#integration" class="btn btn-outline-custom btn-lg">Я поставщик</a>
                     </div>
                  </div>
               </div>
               <div class="col-lg-6"></div>
            </div>
         </div>
      </section>
      <!-- Возможности -->
      <section id="features" class="py-5">
         <div class="container">
            <div class="text-center mb-5">
               <h2 class="section-title">Ключевые возможности портала</h2>
               <p class="lead">Решения для эффективной работы на строительном рынке</p>
            </div>
            <div class="row g-4">
               <div class="col-md-6 col-lg-4">
                  <div class="feature-card">
                     <div class="feature-icon">
                        <i class="bi bi-search"></i>
                     </div>
                     <h4>Умный поиск</h4>
                     <p>Единая строка поиска по названию, ГОСТу, артикулу. Быстрый поиск нужных материалов по всей базе поставщиков.</p>
                  </div>
               </div>
               <div class="col-md-6 col-lg-4">
                  <div class="feature-card">
                     <div class="feature-icon">
                        <i class="bi bi-funnel"></i>
                     </div>
                     <h4>Точная фильтрация</h4>
                     <p>Фильтрация по региону поставки, цене, объему на складе, производителю. Найдите именно то, что вам нужно.</p>
                  </div>
               </div>
               <div class="col-md-6 col-lg-4">
                  <div class="feature-card">
                     <div class="feature-icon">
                        <i class="bi bi-box-seam"></i>
                     </div>
                     <h4>Актуальные остатки</h4>
                     <p>Реальные данные о наличии товаров на складах поставщиков. Больше никаких сюрпризов при заказе.</p>
                  </div>
               </div>
               <div class="col-md-6 col-lg-4">
                  <div class="feature-card">
                     <div class="feature-icon">
                        <i class="bi bi-cart-check"></i>
                     </div>
                     <h4>Простое оформление</h4>
                     <p>Минимальное количество полей при заказе. Заказ уходит напрямую поставщику для выставления счета.</p>
                  </div>
               </div>
               <div class="col-md-6 col-lg-4">
                  <div class="feature-card">
                     <div class="feature-icon">
                        <i class="bi bi-file-earmark-text"></i>
                     </div>
                     <h4>История заказов</h4>
                     <p>Полный архив всех заказов в личном кабинете. Удобный отслеживание статусов и управление закупками.</p>
                  </div>
               </div>
               <div class="col-md-6 col-lg-4">
                  <div class="feature-card">
                     <div class="feature-icon">
                        <i class="bi bi-gear"></i>
                     </div>
                     <h4>Управление каталогом</h4>
                     <p>Простой личный кабинет для поставщиков. Ручная загрузка или автоматическая синхронизация с 1С.</p>
                  </div>
               </div>
            </div>
         </div>
      </section>
      <!-- Аналитика проектной документации -->
      <section id="analytics" class="analytics-section">
         <div class="container">
            <div class="text-center mb-5">
               <h2 class="section-title">Аналитика проектной документации</h2>
               <p class="lead">ИИ-анализ, калькуляция себестоимости и подбор поставщиков</p>
            </div>
            <div class="analytics-card">
               <div class="dashboard-header">
                  <h3 class="dashboard-title">Анализ проекта <span class="ai-badge"><i class="bi bi-cpu"></i>ИИ</span></h3>
                  <button class="btn btn-primary-custom" data-bs-toggle="modal" data-bs-target="#uploadModal">
                  <i class="bi bi-cloud-upload me-2"></i>Загрузить документы
                  </button>
               </div>
               <div class="upload-area" id="uploadArea">
                  <div class="upload-icon">
                     <i class="bi bi-file-earmark-arrow-up"></i>
                  </div>
                  <h4>Загрузите проектную документацию</h4>
                  <p class="text-muted">Перетащите файлы сюда или нажмите для выбора</p>
                  <button class="btn btn-outline-custom mt-3">Выбрать файлы</button>
                  <div class="file-types">
                     <div class="file-type"><i class="bi bi-file-pdf"></i>PDF</div>
                     <div class="file-type"><i class="bi bi-file-word"></i>DOCX</div>
                     <div class="file-type"><i class="bi bi-file-excel"></i>Excel</div>
                     <div class="file-type"><i class="bi bi-file-image"></i>Чертежи</div>
                  </div>
               </div>
               <div class="analysis-progress" id="analysisProgress">
                  <h5 class="mb-3">Анализ документации...</h5>
                  <div class="progress">
                     <div class="progress-bar" role="progressbar" style="width: 0%"></div>
                  </div>
                  <div class="analysis-steps">
                     <div class="step active" id="step1">
                        <div class="step-icon">1</div>
                        <div>
                           <strong>Распознавание документов</strong>
                           <div class="text-muted">OCR и извлечение текста</div>
                        </div>
                     </div>
                     <div class="step" id="step2">
                        <div class="step-icon">2</div>
                        <div>
                           <strong>Анализ спецификаций</strong>
                           <div class="text-muted">NLP-обработка и структурирование</div>
                        </div>
                     </div>
                     <div class="step" id="step3">
                        <div class="step-icon">3</div>
                        <div>
                           <strong>Калькуляция себестоимости</strong>
                           <div class="text-muted">Расчет текущих цен и прогноз</div>
                        </div>
                     </div>
                     <div class="step" id="step4">
                        <div class="step-icon">4</div>
                        <div>
                           <strong>Подбор поставщиков</strong>
                           <div class="text-muted">ИИ-сопоставление и рекомендации</div>
                        </div>
                     </div>
                  </div>
               </div>
               <div class="results-section" id="resultsSection">
                  <div class="cost-summary">
                     <h4 class="mb-4">Калькуляция себестоимости проекта</h4>
                     <div class="cost-item">
                        <span>Базовая смета</span>
                        <div>
                           <span class="cost-value">12 450 000 ₽</span>
                        </div>
                     </div>
                     <div class="cost-item">
                        <span>Текущая стоимость материалов</span>
                        <div>
                           <span class="cost-value">13 820 000 ₽</span>
                           <span class="cost-deviation deviation-up">+11%</span>
                        </div>
                     </div>
                     <div class="cost-item">
                        <span>Прогноз на 3 месяца</span>
                        <div>
                           <span class="cost-value">14 650 000 ₽</span>
                           <span class="cost-deviation deviation-up">+18%</span>
                        </div>
                     </div>
                     <div class="cost-item">
                        <span>Оптимальная стоимость с подбором поставщиков</span>
                        <div>
                           <span class="cost-value">13 150 000 ₽</span>
                           <span class="cost-deviation deviation-down">-5%</span>
                        </div>
                     </div>
                  </div>
                  <div class="materials-table">
                     <table class="table table-hover mb-0">
                        <thead>
                           <tr>
                              <th>Материал</th>
                              <th>Объем</th>
                              <th>Базовая цена</th>
                              <th>Текущая цена</th>
                              <th>Тренд</th>
                              <th>Прогноз</th>
                              <th>Действия</th>
                           </tr>
                        </thead>
                        <tbody>
                           <tr>
                              <td><strong>Цемент М500 Д0</strong></td>
                              <td>250 тонн</td>
                              <td>4 500 ₽/т</td>
                              <td>4 850 ₽/т</td>
                              <td><span class="price-trend trend-up">+7.8%</span></td>
                              <td>5 100 ₽/т</td>
                              <td>
                                 <button class="btn btn-sm btn-outline-custom">Найти поставщиков</button>
                              </td>
                           </tr>
                           <tr>
                              <td><strong>Арматура А500С 12мм</strong></td>
                              <td>85 тонн</td>
                              <td>48 000 ₽/т</td>
                              <td>52 300 ₽/т</td>
                              <td><span class="price-trend trend-up">+9.0%</span></td>
                              <td>54 500 ₽/т</td>
                              <td>
                                 <button class="btn btn-sm btn-outline-custom">Найти поставщиков</button>
                              </td>
                           </tr>
                           <tr>
                              <td><strong>Бетон B25</strong></td>
                              <td>1 200 м³</td>
                              <td>3 800 ₽/м³</td>
                              <td>4 050 ₽/м³</td>
                              <td><span class="price-trend trend-up">+6.6%</span></td>
                              <td>4 200 ₽/м³</td>
                              <td>
                                 <button class="btn btn-sm btn-outline-custom">Найти поставщиков</button>
                              </td>
                           </tr>
                           <tr>
                              <td><strong>Кирпич рядовой М150</strong></td>
                              <td>150 000 шт</td>
                              <td>13 500 ₽/т.шт</td>
                              <td>14 200 ₽/т.шт</td>
                              <td><span class="price-trend trend-up">+5.2%</span></td>
                              <td>14 800 ₽/т.шт</td>
                              <td>
                                 <button class="btn btn-sm btn-outline-custom">Найти поставщиков</button>
                              </td>
                           </tr>
                        </tbody>
                     </table>
                  </div>
                  <div class="forecast-chart">
                     <div class="chart-placeholder">
                        <i class="bi bi-graph-up"></i>
                        <p>График прогноза цен на материалы</p>
                     </div>
                  </div>
                  <div class="suppliers-section">
                     <h4 class="mb-4">Рекомендованные поставщики <span class="ai-badge"><i class="bi bi-cpu"></i>ИИ</span></h4>
                     <div class="row">
                        <div class="col-lg-6 mb-4">
                           <div class="supplier-card">
                              <div class="supplier-header">
                                 <div>
                                    <div class="supplier-name">ООО "СтройРесурс"</div>
                                    <div class="supplier-rating">
                                       <i class="bi bi-star-fill"></i>
                                       <i class="bi bi-star-fill"></i>
                                       <i class="bi bi-star-fill"></i>
                                       <i class="bi bi-star-fill"></i>
                                       <i class="bi bi-star-half"></i>
                                       <span class="ms-2">4.7</span>
                                    </div>
                                 </div>
                                 <div class="position-relative">
                                    <span class="badge bg-success">Оптимальное предложение</span>
                                    <span class="notification-badge">3</span>
                                 </div>
                              </div>
                              <div class="supplier-details">
                                 <div class="detail-item">
                                    <i class="bi bi-geo-alt detail-icon"></i>
                                    <span>Москва и МО</span>
                                 </div>
                                 <div class="detail-item">
                                    <i class="bi bi-truck detail-icon"></i>
                                    <span>Доставка 1-3 дня</span>
                                 </div>
                                 <div class="detail-item">
                                    <i class="bi bi-piggy-bank detail-icon"></i>
                                    <span>Скидка 5% при заказе от 50т</span>
                                 </div>
                                 <div class="detail-item">
                                    <i class="bi bi-shield-check detail-icon"></i>
                                    <span>Гарантия качества</span>
                                 </div>
                              </div>
                              <div class="supplier-actions">
                                 <button class="btn-request">Отправить запрос</button>
                                 <button class="btn-contact">Связаться</button>
                              </div>
                           </div>
                        </div>
                        <div class="col-lg-6 mb-4">
                           <div class="supplier-card">
                              <div class="supplier-header">
                                 <div>
                                    <div class="supplier-name">АО "ЦементПром"</div>
                                    <div class="supplier-rating">
                                       <i class="bi bi-star-fill"></i>
                                       <i class="bi bi-star-fill"></i>
                                       <i class="bi bi-star-fill"></i>
                                       <i class="bi bi-star-fill"></i>
                                       <i class="bi bi-star"></i>
                                       <span class="ms-2">4.2</span>
                                    </div>
                                 </div>
                                 <span class="badge bg-warning">Производитель</span>
                              </div>
                              <div class="supplier-details">
                                 <div class="detail-item">
                                    <i class="bi bi-geo-alt detail-icon"></i>
                                    <span>Рязанская обл.</span>
                                 </div>
                                 <div class="detail-item">
                                    <i class="bi bi-truck detail-icon"></i>
                                    <span>Доставка 3-5 дней</span>
                                 </div>
                                 <div class="detail-item">
                                    <i class="bi bi-piggy-bank detail-icon"></i>
                                    <span>Цена производителя</span>
                                 </div>
                                 <div class="detail-item">
                                    <i class="bi bi-recycle detail-icon"></i>
                                    <span>Собственное производство</span>
                                 </div>
                              </div>
                              <div class="supplier-actions">
                                 <button class="btn-request">Отправить запрос</button>
                                 <button class="btn-contact">Связаться</button>
                              </div>
                           </div>
                        </div>
                     </div>
                  </div>
               </div>
            </div>
         </div>
      </section>
      <!-- ИИ-Модуль "Поиск Поставщика" -->
      <section id="supplier-search" class="supplier-search-section">
         <div class="container">
            <div class="text-center mb-5">
               <h2 class="section-title">ИИ-Модуль "Поиск Поставщика"</h2>
               <p class="lead">Умное сопоставление потребностей проекта с оптимальными поставщиками</p>
            </div>
            <div class="search-filters">
               <h3 class="mb-4">Параметры поиска <span class="ai-badge"><i class="bi bi-cpu"></i>ИИ</span></h3>
               <div class="row">
                  <div class="col-md-6">
                     <div class="filter-group">
                        <div class="filter-label">
                           <i class="bi bi-box-seam"></i>Материал
                        </div>
                        <select class="form-select">
                           <option selected>Цемент М500 Д0</option>
                           <option>Арматура А500С 12мм</option>
                           <option>Бетон B25</option>
                           <option>Кирпич рядовой М150</option>
                        </select>
                     </div>
                  </div>
                  <div class="col-md-6">
                     <div class="filter-group">
                        <div class="filter-label">
                           <i class="bi bi-calculator"></i>Объем
                        </div>
                        <div class="input-group">
                           <input type="number" class="form-control" value="250" placeholder="Объем">
                           <span class="input-group-text">тонн</span>
                        </div>
                     </div>
                  </div>
                  <div class="col-md-6">
                     <div class="filter-group">
                        <div class="filter-label">
                           <i class="bi bi-calendar3"></i>Срок поставки
                        </div>
                        <input type="date" class="form-control" value="2024-02-15">
                     </div>
                  </div>
                  <div class="col-md-6">
                     <div class="filter-group">
                        <div class="filter-label">
                           <i class="bi bi-geo-alt"></i>Геолокация объекта
                        </div>
                        <input type="text" class="form-control" value="г. Москва, ул. Строительная, 15" placeholder="Адрес объекта">
                     </div>
                  </div>
                  <div class="col-md-6">
                     <div class="filter-group">
                        <div class="filter-label">
                           <i class="bi bi-shield-check"></i>Требования к сертификации
                        </div>
                        <select class="form-select">
                           <option selected>ГОСТ 31108-2016</option>
                           <option>ГОСТ Р 53786-2010</option>
                           <option>Технические условия</option>
                           <option>Без требований</option>
                        </select>
                     </div>
                  </div>
                  <div class="col-md-6">
                     <div class="filter-group">
                        <div class="filter-label">
                           <i class="bi bi-truck"></i>Логистика
                        </div>
                        <select class="form-select">
                           <option selected>Самовывоз</option>
                           <option>Доставка поставщиком</option>
                           <option>Любой вариант</option>
                        </select>
                     </div>
                  </div>
               </div>
               <div class="optimization-options">
                  <div class="optimization-card selected" data-opt="cost">
                     <div class="optimization-icon">
                        <i class="bi bi-cash"></i>
                     </div>
                     <div class="optimization-title">Мин. стоимость</div>
                     <div class="optimization-desc">Оптимальная цена с учетом всех факторов</div>
                  </div>
                  <div class="optimization-card" data-opt="time">
                     <div class="optimization-icon">
                        <i class="bi bi-clock-history"></i>
                     </div>
                     <div class="optimization-title">Мин. срок</div>
                     <div class="optimization-desc">Быстрая поставка в сжатые сроки</div>
                  </div>
                  <div class="optimization-card" data-opt="balance">
                     <div class="optimization-icon">
                        <i class="bi bi-balance-scale"></i>
                     </div>
                     <div class="optimization-title">Оптимальный баланс</div>
                     <div class="optimization-desc">Лучшее соотношение цена/качество/срок</div>
                  </div>
               </div>
               <div class="text-center mt-4">
                  <button class="btn btn-primary-custom btn-lg" onclick="startSupplierSearch()">
                  <i class="bi bi-search me-2"></i>Найти поставщиков
                  </button>
               </div>
            </div>
            <div class="search-results" id="searchResults">
               <div class="result-header">
                  <h3>Результаты поиска поставщиков</h3>
                  <div class="result-summary">
                     <div class="summary-item">
                        <div class="summary-value">12</div>
                        <div class="summary-label">Найдено поставщиков</div>
                     </div>
                     <div class="summary-item">
                        <div class="summary-value">4 720 ₽</div>
                        <div class="summary-label">Средняя цена</div>
                     </div>
                     <div class="summary-item">
                        <div class="summary-value">3 дня</div>
                        <div class="summary-label">Средний срок</div>
                     </div>
                     <div class="summary-item">
                        <div class="summary-value">98%</div>
                        <div class="summary-label">Соответствие</div>
                     </div>
                  </div>
               </div>
               <div class="row">
                  <div class="col-lg-6 mb-4">
                     <div class="supplier-match-card">
                        <div class="match-header">
                           <div>
                              <div class="supplier-name">ООО "СтройРесурс"</div>
                              <div class="supplier-rating">
                                 <i class="bi bi-star-fill"></i>
                                 <i class="bi bi-star-fill"></i>
                                 <i class="bi bi-star-fill"></i>
                                 <i class="bi bi-star-fill"></i>
                                 <i class="bi bi-star-half"></i>
                                 <span class="ms-2">4.7</span>
                              </div>
                           </div>
                           <div class="match-score">95% совпадение</div>
                        </div>
                        <div class="match-details">
                           <div class="match-detail">
                              <span class="detail-label">Цена</span>
                              <span class="detail-value">4 650 ₽/т</span>
                           </div>
                           <div class="match-detail">
                              <span class="detail-label">Срок</span>
                              <span class="detail-value">2 дня</span>
                           </div>
                           <div class="match-detail">
                              <span class="detail-label">Остаток</span>
                              <span class="detail-value">300 т</span>
                           </div>
                           <div class="match-detail">
                              <span class="detail-label">Рейтинг</span>
                              <span class="detail-value">4.7/5</span>
                           </div>
                        </div>
                        <div class="risk-alert medium">
                           <i class="bi bi-exclamation-triangle"></i>
                           <div>
                              <strong>Средний риск:</strong> Поставщик имеет загруженность в указанные сроки. Рекомендуется подтвердить наличие.
                           </div>
                        </div>
                        <div class="match-actions">
                           <button class="btn-request">Отправить запрос</button>
                           <button class="btn-contact">Связаться</button>
                           <button class="btn btn-outline-custom btn-small">Детали</button>
                        </div>
                     </div>
                  </div>
                  <div class="col-lg-6 mb-4">
                     <div class="supplier-match-card risk-high">
                        <div class="match-header">
                           <div>
                              <div class="supplier-name">АО "ЦементПром"</div>
                              <div class="supplier-rating">
                                 <i class="bi bi-star-fill"></i>
                                 <i class="bi bi-star-fill"></i>
                                 <i class="bi bi-star-fill"></i>
                                 <i class="bi bi-star-fill"></i>
                                 <i class="bi bi-star"></i>
                                 <span class="ms-2">4.2</span>
                              </div>
                           </div>
                           <div class="match-score medium">78% совпадение</div>
                        </div>
                        <div class="match-details">
                           <div class="match-detail">
                              <span class="detail-label">Цена</span>
                              <span class="detail-value">4 500 ₽/т</span>
                           </div>
                           <div class="match-detail">
                              <span class="detail-label">Срок</span>
                              <span class="detail-value">5 дней</span>
                           </div>
                           <div class="match-detail">
                              <span class="detail-label">Остаток</span>
                              <span class="detail-value">500 т</span>
                           </div>
                           <div class="match-detail">
                              <span class="detail-label">Рейтинг</span>
                              <span class="detail-value">4.2/5</span>
                           </div>
                        </div>
                        <div class="risk-alert">
                           <i class="bi bi-exclamation-circle"></i>
                           <div>
                              <strong>Высокий риск срыва сроков:</strong> Длительная логистика из Рязанской области. Учитывайте возможные задержки.
                           </div>
                        </div>
                        <div class="match-actions">
                           <button class="btn-request">Отправить запрос</button>
                           <button class="btn-contact">Связаться</button>
                           <button class="btn btn-outline-custom btn-small">Детали</button>
                        </div>
                     </div>
                  </div>
               </div>
               <div class="comparison-table">
                  <table class="table table-hover mb-0">
                     <thead>
                        <tr>
                           <th>Поставщик</th>
                           <th>Цена</th>
                           <th>Срок поставки</th>
                           <th>Остаток</th>
                           <th>Рейтинг</th>
                           <th>Совпадение</th>
                           <th>Риск</th>
                           <th>Действия</th>
                        </tr>
                     </thead>
                     <tbody>
                        <tr>
                           <td><strong>ООО "СтройРесурс"</strong></td>
                           <td class="price-cell">4 650 ₽/т</td>
                           <td class="time-cell">2 дня</td>
                           <td>300 т</td>
                           <td class="rating-cell">4.7/5</td>
                           <td><span class="badge bg-success">95%</span></td>
                           <td><span class="badge bg-warning">Средний</span></td>
                           <td>
                              <button class="btn btn-sm btn-outline-custom">Выбрать</button>
                           </td>
                        </tr>
                        <tr>
                           <td><strong>ООО "МеталлТрейд"</strong></td>
                           <td class="price-cell">4 800 ₽/т</td>
                           <td class="time-cell">1 день</td>
                           <td>150 т</td>
                           <td class="rating-cell">5.0/5</td>
                           <td><span class="badge bg-success">92%</span></td>
                           <td><span class="badge bg-success">Низкий</span></td>
                           <td>
                              <button class="btn btn-sm btn-outline-custom">Выбрать</button>
                           </td>
                        </tr>
                     </tbody>
                  </table>
               </div>
               <div class="map-container">
                  <div class="map-placeholder">
                     <i class="bi bi-map"></i>
                     <p>Карта расположения поставщиков и объекта</p>
                  </div>
               </div>
            </div>
         </div>
      </section>
      <!-- Градостроительный Ассистент -->
      <section id="urban-assistant" class="urban-assistant-section">
         <div class="container">
            <div class="text-center mb-5">
               <h2 class="section-title">Градостроительный Ассистент <span class="ai-badge"><i class="bi bi-cpu"></i>ИИ</span></h2>
               <p class="lead">Оперативная оценка градостроительного потенциала земельных участков</p>
            </div>
            <div class="assistant-card">
               <div class="assistant-header">
                  <h3>Анализ земельного участка</h3>
                  <p>Введите кадастровый номер или выберите участок на карте для анализа</p>
               </div>
               <div class="assistant-form">
                  <div class="row">
                     <div class="col-md-8">
                        <div class="input-group">
                           <input type="text" class="form-control" id="cadastralNumber" placeholder="Кадастровый номер (например: 50:21:0100201:1234)">
                           <button class="btn btn-primary-custom" type="button" onclick="analyzePlot()">Анализировать</button>
                        </div>
                     </div>
                     <div class="col-md-4">
                        <button class="btn btn-outline-custom w-100" type="button" onclick="showMapSelector()">
                        <i class="bi bi-map me-2"></i>Выбрать на карте
                        </button>
                     </div>
                  </div>
                  <div class="map-selector" id="mapSelector" style="display: none;">
                     <div class="map-placeholder">
                        <i class="bi bi-map"></i>
                        <p>Интерактивная карта для выбора участка</p>
                        <button class="btn btn-sm btn-primary-custom mt-2">Выбрать участок</button>
                     </div>
                  </div>
               </div>
               <div class="assistant-results" id="assistantResults" style="display: none;">
                  <ul class="nav nav-tabs" id="resultTabs" role="tablist">
                     <li class="nav-item" role="presentation">
                        <button class="nav-link active" id="basic-tab" data-bs-toggle="tab" data-bs-target="#basic" type="button" role="tab">Основные параметры</button>
                     </li>
                     <li class="nav-item" role="presentation">
                        <button class="nav-link" id="restrictions-tab" data-bs-toggle="tab" data-bs-target="#restrictions" type="button" role="tab">Ограничения</button>
                     </li>
                     <li class="nav-item" role="presentation">
                        <button class="nav-link" id="infrastructure-tab" data-bs-toggle="tab" data-bs-target="#infrastructure" type="button" role="tab">Инфраструктура</button>
                     </li>
                     <li class="nav-item" role="presentation">
                        <button class="nav-link" id="recommendations-tab" data-bs-toggle="tab" data-bs-target="#recommendations" type="button" role="tab">Рекомендации</button>
                     </li>
                  </ul>
                  <div class="tab-content" id="resultTabsContent">
                     <div class="tab-pane fade show active" id="basic" role="tabpanel">
                        <div class="plot-map">
                           <div class="map-placeholder">
                              <i class="bi bi-map"></i>
                              <p>Карта участка с границами и зонированием</p>
                           </div>
                        </div>
                        <div class="plot-parameters">
                           <h4>Основные параметры участка</h4>
                           <div class="row">
                              <div class="col-md-6">
                                 <table class="table table-borderless">
                                    <tr>
                                       <td><strong>Кадастровый номер:</strong></td>
                                       <td id="resultCadastral">50:21:0100201:1234</td>
                                    </tr>
                                    <tr>
                                       <td><strong>Площадь:</strong></td>
                                       <td id="resultArea">2 500 м²</td>
                                    </tr>
                                    <tr>
                                       <td><strong>Категория земель:</strong></td>
                                       <td id="resultCategory">Земли населенных пунктов</td>
                                    </tr>
                                    <tr>
                                       <td><strong>ВРИ (основной):</strong></td>
                                       <td id="resultVRI">ИЖС</td>
                                    </tr>
                                 </table>
                              </div>
                              <div class="col-md-6">
                                 <table class="table table-borderless">
                                    <tr>
                                       <td><strong>Территориальная зона:</strong></td>
                                       <td id="resultZone">Ж-1 (Зона застройки индивидуальными жилыми домами)</td>
                                    </tr>
                                    <tr>
                                       <td><strong>Плотность застройки:</strong></td>
                                       <td id="resultDensity">30%</td>
                                    </tr>
                                    <tr>
                                       <td><strong>Макс. этажность:</strong></td>
                                       <td id="resultFloors">3 этажа</td>
                                    </tr>
                                    <tr>
                                       <td><strong>Макс. процент застройки:</strong></td>
                                       <td id="resultBuildPercent">40%</td>
                                    </tr>
                                 </table>
                              </div>
                           </div>
                           <div class="potential-metrics">
                              <h4>Потенциал участка</h4>
                              <div class="row">
                                 <div class="col-md-3">
                                    <div class="metric-card">
                                       <div class="metric-value">1 000 м²</div>
                                       <div class="metric-label">Площадь застройки</div>
                                    </div>
                                 </div>
                                 <div class="col-md-3">
                                    <div class="metric-card">
                                       <div class="metric-value">3 000 м²</div>
                                       <div class="metric-label">Общая площадь</div>
                                    </div>
                                 </div>
                                 <div class="col-md-3">
                                    <div class="metric-card">
                                       <div class="metric-value">85%</div>
                                       <div class="metric-label">Подъездность</div>
                                    </div>
                                 </div>
                                 <div class="col-md-3">
                                    <div class="metric-card">
                                       <div class="metric-value">2.5</div>
                                       <div class="metric-label">Индекс привлекательности</div>
                                    </div>
                                 </div>
                              </div>
                           </div>
                        </div>
                     </div>
                     <div class="tab-pane fade" id="restrictions" role="tabpanel">
                        <h4>Ограничения и риски</h4>
                        <div class="restrictions-summary">
                           <div class="alert alert-warning d-flex align-items-center" role="alert">
                              <i class="bi bi-exclamation-triangle-fill me-2"></i>
                              <div>
                                 Обнаружено 3 ограничения и 2 риска для застройки участка. Рекомендуется учесть их при планировании.
                              </div>
                           </div>
                        </div>
                        <div class="restrictions-list">
                           <div class="restriction-item high-risk">
                              <div class="restriction-header">
                                 <div class="restriction-title">Санитарно-защитная зона промышленного предприятия</div>
                                 <div class="restriction-badge">Высокий риск</div>
                              </div>
                              <div class="restriction-details">
                                 <p>Участок частично попадает в СЗЗ предприятия "СтройМаш" (шириной 500 м). Запрещено строительство жилых объектов в этой зоне.</p>
                                 <div class="restriction-solution">
                                    <strong>Решение:</strong> Необходимо получить согласование с Роспотребнадзором или изменить проект застройки.
                                 </div>
                              </div>
                           </div>
                           <div class="restriction-item medium-risk">
                              <div class="restriction-header">
                                 <div class="restriction-title">Охранная зона ЛЭП</div>
                                 <div class="restriction-badge">Средний риск</div>
                              </div>
                              <div class="restriction-details">
                                 <p>По западной границе участка проходит охранная зона ЛЭП 110 кВ (шириной 20 м). Запрещено строительство в этой зоне.</p>
                                 <div class="restriction-solution">
                                    <strong>Решение:</strong> Соблюдать минимальные отступы от ЛЭП при проектировании.
                                 </div>
                              </div>
                           </div>
                           <div class="restriction-item low-risk">
                              <div class="restriction-header">
                                 <div class="restriction-title">Зона с особыми условиями использования территории</div>
                                 <div class="restriction-badge">Низкий риск</div>
                              </div>
                              <div class="restriction-details">
                                 <p>Участок находится в водоохранной зоне реки (шириной 50 м от уреза воды). Требуется соблюдение экологических норм.</p>
                                 <div class="restriction-solution">
                                    <strong>Решение:</strong> Необходимо согласование с Росприроднадзором, использование экологичных материалов и технологий.
                                 </div>
                              </div>
                           </div>
                        </div>
                        <div class="geology-risks">
                           <h5>Геологические риски</h5>
                           <div class="row">
                              <div class="col-md-6">
                                 <div class="risk-indicator">
                                    <div class="risk-title">Уровень грунтовых вод</div>
                                    <div class="risk-bar">
                                       <div class="risk-progress" style="width: 40%; background-color: var(--warning-color);"></div>
                                    </div>
                                    <div class="risk-value">1.8 м</div>
                                 </div>
                              </div>
                              <div class="col-md-6">
                                 <div class="risk-indicator">
                                    <div class="risk-title">Риск подтопления</div>
                                    <div class="risk-bar">
                                       <div class="risk-progress" style="width: 25%; background-color: var(--success-color);"></div>
                                    </div>
                                    <div class="risk-value">Низкий</div>
                                 </div>
                              </div>
                           </div>
                        </div>
                     </div>
                     <div class="tab-pane fade" id="infrastructure" role="tabpanel">
                        <h4>Инфраструктура и доступность</h4>
                        <div class="infrastructure-map">
                           <div class="map-placeholder">
                              <i class="bi bi-map"></i>
                              <p>Карта инфраструктуры вокруг участка</p>
                           </div>
                        </div>
                        <div class="infrastructure-metrics">
                           <div class="row">
                              <div class="col-md-6">
                                 <h5>Транспортная доступность</h5>
                                 <table class="table table-sm">
                                    <tr>
                                       <td>Ближайшая остановка общественного транспорта</td>
                                       <td>350 м</td>
                                    </tr>
                                    <tr>
                                       <td>Ближайшая магистраль</td>
                                       <td>ул. Центральная (800 м)</td>
                                    </tr>
                                    <tr>
                                       <td>Доступность к центру города</td>
                                       <td>15 минут на авто</td>
                                    </tr>
                                    <tr>
                                       <td>Оценка подъездности</td>
                                       <td><span class="badge bg-success">Хорошая</span></td>
                                    </tr>
                                 </table>
                              </div>
                              <div class="col-md-6">
                                 <h5>Инженерные сети</h5>
                                 <table class="table table-sm">
                                    <tr>
                                       <td>Электроснабжение</td>
                                       <td><i class="bi bi-check-circle-fill text-success"></i> На границе участка</td>
                                    </tr>
                                    <tr>
                                       <td>Водоснабжение</td>
                                       <td><i class="bi bi-check-circle-fill text-success"></i> 150 м</td>
                                    </tr>
                                    <tr>
                                       <td>Газоснабжение</td>
                                       <td><i class="bi bi-check-circle-fill text-success"></i> 200 м</td>
                                    </tr>
                                    <tr>
                                       <td>Канализация</td>
                                       <td><i class="bi bi-exclamation-circle-fill text-warning"></i> Требуется локальная</td>
                                    </tr>
                                 </table>
                              </div>
                           </div>
                        </div>
                        <div class="social-infrastructure">
                           <h5>Социальная инфраструктура</h5>
                           <div class="row">
                              <div class="col-md-4">
                                 <div class="infra-item">
                                    <i class="bi bi-building"></i>
                                    <div class="infra-name">Школа</div>
                                    <div class="infra-distance">1.2 км</div>
                                 </div>
                              </div>
                              <div class="col-md-4">
                                 <div class="infra-item">
                                    <i class="bi bi-hospital"></i>
                                    <div class="infra-name">Поликлиника</div>
                                    <div class="infra-distance">2.5 км</div>
                                 </div>
                              </div>
                              <div class="col-md-4">
                                 <div class="infra-item">
                                    <i class="bi bi-cart3"></i>
                                    <div class="infra-name">Магазин</div>
                                    <div class="infra-distance">500 м</div>
                                 </div>
                              </div>
                           </div>
                        </div>
                     </div>
                     <div class="tab-pane fade" id="recommendations" role="tabpanel">
                        <h4>Рекомендации по использованию участка</h4>
                        <div class="vri-comparison">
                           <h5>Оценка привлекательности ВРИ</h5>
                           <div class="table-responsive">
                              <table class="table table-hover">
                                 <thead>
                                    <tr>
                                       <th>Вид разрешенного использования</th>
                                       <th>Потенциал</th>
                                       <th>Риски</th>
                                       <th>Рекомендация</th>
                                    </tr>
                                 </thead>
                                 <tbody>
                                    <tr>
                                       <td><strong>ИЖС (индивидуальное жилищное строительство)</strong></td>
                                       <td>
                                          <div class="progress">
                                             <div class="progress-bar" style="width: 75%; background-color: var(--success-color);"></div>
                                          </div>
                                       </td>
                                       <td>
                                          <div class="progress">
                                             <div class="progress-bar" style="width: 40%; background-color: var(--warning-color);"></div>
                                          </div>
                                       </td>
                                       <td><span class="badge bg-success">Рекомендуется</span></td>
                                    </tr>
                                    <tr>
                                       <td><strong>Дачное строительство</strong></td>
                                       <td>
                                          <div class="progress">
                                             <div class="progress-bar" style="width: 60%; background-color: var(--warning-color);"></div>
                                          </div>
                                       </td>
                                       <td>
                                          <div class="progress">
                                             <div class="progress-bar" style="width: 30%; background-color: var(--success-color);"></div>
                                          </div>
                                       </td>
                                       <td><span class="badge bg-warning">Возможно</span></td>
                                    </tr>
                                    <tr>
                                       <td><strong>Малоэтажная застройка (до 4 этажей)</strong></td>
                                       <td>
                                          <div class="progress">
                                             <div class="progress-bar" style="width: 90%; background-color: var(--success-color);"></div>
                                          </div>
                                       </td>
                                       <td>
                                          <div class="progress">
                                             <div class="progress-bar" style="width: 70%; background-color: var(--danger-color);"></div>
                                          </div>
                                       </td>
                                       <td><span class="badge bg-danger">Не рекомендуется</span></td>
                                    </tr>
                                 </tbody>
                              </table>
                           </div>
                        </div>
                        <div class="development-recommendations">
                           <h5>Рекомендации по застройке</h5>
                           <div class="recommendation-card">
                              <div class="recommendation-header">
                                 <div class="recommendation-title">Оптимальная концепция застройки</div>
                                 <div class="recommendation-score">8.5/10</div>
                              </div>
                              <div class="recommendation-body">
                                 <p>Рекомендуется строительство жилого дома площадью до 300 м² с мансардным этажом. Оптимальное расположение дома - северная часть участка для минимизации влияния СЗЗ.</p>
                                 <ul>
                                    <li>Фундамент - монолитная плита (из-за высокого УГВ)</li>
                                    <li>Материал стен - газобетон или дерево</li>
                                    <li>Кровля - металлочерепица или гибкая черепица</li>
                                    <li>Система канализации - локальная (септик)</li>
                                 </ul>
                              </div>
                           </div>
                           <div class="recommendation-steps">
                              <h6>План действий:</h6>
                              <ol>
                                 <li>Получение градостроительного плана земельного участка (ГПЗУ)</li>
                                 <li>Проведение геологических изысканий</li>
                                 <li>Разработка архитектурного проекта с учетом ограничений</li>
                                 <li>Согласование проекта с надзорными органами</li>
                                 <li>Получение разрешения на строительство</li>
                              </ol>
                           </div>
                        </div>
                        <div class="action-buttons">
                           <button class="btn btn-primary-custom">Скачать полный отчет</button>
                           <button class="btn btn-outline-custom">Консультация специалиста</button>
                           <button class="btn btn-outline-custom">Подобрать проект</button>
                        </div>
                     </div>
                  </div>
               </div>
            </div>
         </div>
      </section>
      <!-- Панель уведомлений о рисках -->
      <div class="notification-panel" id="notificationPanel">
         <div class="notification-header">
            <h5 class="mb-0">Уведомления о рисках</h5>
            <button class="btn-close btn-close-white" onclick="closeNotifications()"></button>
         </div>
         <div class="notification-list" id="notificationList">
            <div class="notification-item high-risk">
               <div class="d-flex justify-content-between align-items-start">
                  <div>
                     <strong>Высокий риск срыва сроков</strong>
                     <div>Поставщик АО "ЦементПром" может не успеть доставить материалы к указанному сроку из-за удаленности.</div>
                     <div class="notification-time">2 минуты назад</div>
                  </div>
               </div>
            </div>
            <div class="notification-item medium-risk">
               <div class="d-flex justify-content-between align-items-start">
                  <div>
                     <strong>Средний риск дефицита</strong>
                     <div>У ООО "СтройРесурс" ограниченное количество материала на складе. Рекомендуется ускорить оформление заказа.</div>
                     <div class="notification-time">15 минут назад</div>
                  </div>
               </div>
            </div>
            <div class="notification-item success">
               <div class="d-flex justify-content-between align-items-start">
                  <div>
                     <strong>Оптимальный поставщик найден</strong>
                     <div>ООО "МеталлТрейд" соответствует всем требованиям проекта. Рекомендуется к сотрудничеству.</div>
                     <div class="notification-time">1 час назад</div>
                  </div>
               </div>
            </div>
         </div>
      </div>
      <!-- Интеграция с 1С -->
      <section id="integration" class="integration-section">
         <div class="container">
            <div class="text-center mb-5">
               <h2 class="section-title">Интеграция с 1С</h2>
               <p class="lead">Ключевое преимущество портала для автоматизации бизнеса</p>
            </div>
            <div class="row g-4">
               <div class="col-md-4">
                  <div class="integration-card">
                     <div class="integration-level">Базовый уровень</div>
                     <h4>Ручная загрузка</h4>
                     <p>Загрузка прайс-листа в формате Excel/CSV. Подходит для компаний с небольшим ассортиментом.</p>
                     <ul class="list-unstyled mt-3">
                        <li><i class="bi bi-check-circle-fill text-success"></i> Простота использования</li>
                        <li><i class="bi bi-check-circle-fill text-success"></i> Не требует технических навыков</li>
                        <li><i class="bi bi-check-circle-fill text-success"></i> Быстрое начало работы</li>
                     </ul>
                  </div>
               </div>
               <div class="col-md-4">
                  <div class="integration-card">
                     <div class="integration-level">Стандартный уровень</div>
                     <h4>CommerceML</h4>
                     <p>Полуавтоматическая загрузка файла в стандарте CommerceML. Основной способ для большинства поставщиков.</p>
                     <ul class="list-unstyled mt-3">
                        <li><i class="bi bi-check-circle-fill text-success"></i> Стандартный формат для 1С</li>
                        <li><i class="bi bi-check-circle-fill text-success"></i> Поддержка всех полей товара</li>
                        <li><i class="bi bi-check-circle-fill text-success"></i> Обновление остатков и цен</li>
                     </ul>
                  </div>
               </div>
               <div class="col-md-4">
                  <div class="integration-card">
                     <div class="integration-level">Продвинутый уровень</div>
                     <h4>FTP-интеграция</h4>
                     <p>Полная автоматизация через FTP-сервер. Настройка производится один раз, далее работает автоматически.</p>
                     <ul class="list-unstyled mt-3">
                        <li><i class="bi bi-check-circle-fill text-success"></i> Полная автоматизация</li>
                        <li><i class="bi bi-check-circle-fill text-success"></i> Обновление по расписанию</li>
                        <li><i class="bi bi-check-circle-fill text-success"></i> Исключение ошибок</li>
                     </ul>
                  </div>
               </div>
            </div>
            <div class="text-center mt-5">
               <a href="#" class="btn btn-primary-custom btn-lg">Подробнее об интеграции</a>
            </div>
         </div>
      </section>
      <!-- Поиск товаров -->
      <section class="search-section">
         <div class="container">
            <div class="text-center mb-5">
               <h2 class="section-title">Поиск строительных материалов</h2>
               <p class="lead">Найдите нужные материалы у проверенных поставщиков</p>
            </div>
            <div class="search-container">
               <form class="search-form">
                  <input type="text" class="search-input" placeholder="Название, ГОСТ, артикул...">
                  <input type="text" class="search-input" placeholder="Регион поставки...">
                  <button type="submit" class="search-btn">Найти</button>
               </form>
               <div class="filter-tags">
                  <div class="filter-tag active">Все материалы</div>
                  <div class="filter-tag">Цемент</div>
                  <div class="filter-tag">Металлопрокат</div>
                  <div class="filter-tag">Кирпич</div>
                  <div class="filter-tag">Пиломатериалы</div>
                  <div class="filter-tag">Отделочные материалы</div>
                  <div class="filter-tag">Инженерные системы</div>
               </div>
               <div class="row g-4">
                  <div class="col-md-6 col-lg-4">
                     <div class="product-card">
                        <div class="product-img">
                           <i class="bi bi-box"></i>
                        </div>
                        <div class="product-info">
                           <h5 class="product-title">Цемент М500 Д0</h5>
                           <div class="product-meta">
                              <span>ГОСТ 31108-2016</span>
                              <span>Артикул: ЦМ500</span>
                           </div>
                           <div class="product-price">4 850 ₽/тонна</div>
                           <div class="product-supplier">Поставщик: СтройРесурс</div>
                           <button class="add-to-cart">В корзину</button>
                        </div>
                     </div>
                  </div>
                  <div class="col-md-6 col-lg-4">
                     <div class="product-card">
                        <div class="product-img">
                           <i class="bi bi-box"></i>
                        </div>
                        <div class="product-info">
                           <h5 class="product-title">Арматура А500С 12мм</h5>
                           <div class="product-meta">
                              <span>ГОСТ 5781-82</span>
                              <span>Артикул: АР12</span>
                           </div>
                           <div class="product-price">52 300 ₽/тонна</div>
                           <div class="product-supplier">Поставщик: МеталлПром</div>
                           <button class="add-to-cart">В корзину</button>
                        </div>
                     </div>
                  </div>
                  <div class="col-md-6 col-lg-4">
                     <div class="product-card">
                        <div class="product-img">
                           <i class="bi bi-box"></i>
                        </div>
                        <div class="product-info">
                           <h5 class="product-title">Кирпич рядовой М150</h5>
                           <div class="product-meta">
                              <span>ГОСТ 530-2012</span>
                              <span>Артикул: КР150</span>
                           </div>
                           <div class="product-price">14 200 ₽/1000 шт</div>
                           <div class="product-supplier">Поставщик: КирпичЗавод</div>
                           <button class="add-to-cart">В корзину</button>
                        </div>
                     </div>
                  </div>
               </div>
            </div>
         </div>
      </section>
      <!-- Личный кабинет -->
      <section class="dashboard-section">
         <div class="container">
            <div class="text-center mb-5">
               <h2 class="section-title">Личный кабинет</h2>
               <p class="lead">Удобное управление закупками и продажами</p>
            </div>
            <div class="row">
               <div class="col-lg-6 mb-4">
                  <div class="dashboard-card">
                     <div class="dashboard-header">
                        <h3 class="dashboard-title">Кабинет покупателя</h3>
                        <div class="dropdown">
                           <button class="btn btn-sm btn-outline-secondary dropdown-toggle" type="button" data-bs-toggle="dropdown">
                           ООО "СтройГрад"
                           </button>
                           <ul class="dropdown-menu">
                              <li><a class="dropdown-item" href="#">Профиль</a></li>
                              <li><a class="dropdown-item" href="#">Настройки</a></li>
                              <li>
                                 <hr class="dropdown-divider">
                              </li>
                              <li><a class="dropdown-item" href="#">Выход</a></li>
                           </ul>
                        </div>
                     </div>
                     <div class="dashboard-tabs">
                        <div class="dashboard-tab active">Заказы</div>
                        <div class="dashboard-tab">Корзина</div>
                        <div class="dashboard-tab">Избранное</div>
                        <div class="dashboard-tab position-relative">
                           Аналитика проекта
                           <span class="notification-badge">2</span>
                        </div>
                        <div class="dashboard-tab position-relative">
                           Поиск поставщиков
                           <span class="notification-badge">3</span>
                        </div>
                     </div>
                     <div class="order-list">
                        <div class="order-item">
                           <div>
                              <div class="order-id">Заказ #1245</div>
                              <div class="text-muted">Цемент М500 - 20 тонн</div>
                           </div>
                           <div>
                              <div class="order-status status-new">Новый</div>
                              <div class="text-end">97 000 ₽</div>
                           </div>
                        </div>
                        <div class="order-item">
                           <div>
                              <div class="order-id">Заказ #1243</div>
                              <div class="text-muted">Арматура А500С - 5 тонн</div>
                           </div>
                           <div>
                              <div class="order-status status-processing">В работе</div>
                              <div class="text-end">261 500 ₽</div>
                           </div>
                        </div>
                        <div class="order-item">
                           <div>
                              <div class="order-id">Заказ #1240</div>
                              <div class="text-muted">Кирпич М150 - 10 000 шт</div>
                           </div>
                           <div>
                              <div class="order-status status-completed">Завершен</div>
                              <div class="text-end">142 000 ₽</div>
                           </div>
                        </div>
                     </div>
                     <div class="text-center mt-4">
                        <a href="#" class="btn btn-outline-custom">Все заказы</a>
                     </div>
                  </div>
               </div>
               <div class="col-lg-6 mb-4">
                  <div class="dashboard-card">
                     <div class="dashboard-header">
                        <h3 class="dashboard-title">Кабинет поставщика</h3>
                        <div class="dropdown">
                           <button class="btn btn-sm btn-outline-secondary dropdown-toggle" type="button" data-bs-toggle="dropdown">
                           ООО "СтройРесурс"
                           </button>
                           <ul class="dropdown-menu">
                              <li><a class="dropdown-item" href="#">Профиль компании</a></li>
                              <li><a class="dropdown-item" href="#">Настройки</a></li>
                              <li>
                                 <hr class="dropdown-divider">
                              </li>
                              <li><a class="dropdown-item" href="#">Выход</a></li>
                           </ul>
                        </div>
                     </div>
                     <div class="dashboard-tabs">
                        <div class="dashboard-tab active">Заказы</div>
                        <div class="dashboard-tab">Товары</div>
                        <div class="dashboard-tab">Интеграция</div>
                        <div class="dashboard-tab position-relative">
                           Запросы на анализ
                           <span class="notification-badge">5</span>
                        </div>
                        <div class="dashboard-tab position-relative">
                           Предложения по проектам
                           <span class="notification-badge">2</span>
                        </div>
                     </div>
                     <div class="order-list">
                        <div class="order-item">
                           <div>
                              <div class="order-id">Заказ #1245</div>
                              <div class="text-muted">ООО "СтройГрад"</div>
                           </div>
                           <div>
                              <div class="order-status status-new">Новый</div>
                              <div class="text-end">97 000 ₽</div>
                           </div>
                        </div>
                        <div class="order-item">
                           <div>
                              <div class="order-id">Заказ #1242</div>
                              <div class="text-muted">ООО "СтройМастер"</div>
                           </div>
                           <div>
                              <div class="order-status status-processing">В работе</div>
                              <div class="text-end">145 600 ₽</div>
                           </div>
                        </div>
                     </div>
                     <div class="integration-status mt-4">
                        <div class="status-indicator status-active"></div>
                        <div>
                           <strong>Интеграция с 1С:</strong> активна
                           <div class="text-muted">Последняя синхронизация: 15 мин назад</div>
                        </div>
                     </div>
                     <div class="integration-actions">
                        <button class="btn btn-primary-custom btn-small">Обновить каталог</button>
                        <button class="btn btn-outline-custom btn-small">Настройки интеграции</button>
                     </div>
                  </div>
               </div>
            </div>
         </div>
      </section>
      <!-- Тарифы -->
      <section id="pricing" class="py-5">
         <div class="container">
            <div class="text-center mb-5">
               <h2 class="section-title">Бизнес-модель</h2>
               <p class="lead">Простая и справедливая система оплаты</p>
            </div>
            <div class="row g-4">
               <div class="col-md-4">
                  <div class="pricing-card">
                     <div class="plan-name">Базовый</div>
                     <div class="plan-price">0 ₽</div>
                     <p>Идеально для начала работы</p>
                     <ul class="plan-features">
                        <li><i class="bi bi-check-circle-fill"></i> Регистрация на портале</li>
                        <li><i class="bi bi-check-circle-fill"></i> Доступ к каталогу товаров</li>
                        <li><i class="bi bi-check-circle-fill"></i> Размещение до 50 товаров</li>
                        <li><i class="bi bi-check-circle-fill"></i> Ручная загрузка прайсов</li>
                        <li><i class="bi bi-check-circle-fill"></i> Базовая поддержка</li>
                     </ul>
                     <button class="btn btn-outline-custom w-100">Выбрать план</button>
                  </div>
               </div>
               <div class="col-md-4">
                  <div class="pricing-card popular">
                     <div class="plan-name">Стандарт</div>
                     <div class="plan-price">1-3%</div>
                     <p>Комиссия с успешных сделок</p>
                     <ul class="plan-features">
                        <li><i class="bi bi-check-circle-fill"></i> Все функции базового плана</li>
                        <li><i class="bi bi-check-circle-fill"></i> Неограниченное количество товаров</li>
                        <li><i class="bi bi-check-circle-fill"></i> Интеграция CommerceML</li>
                        <li><i class="bi bi-check-circle-fill"></i> Приоритетная поддержка</li>
                        <li><i class="bi bi-check-circle-fill"></i> Аналитика продаж</li>
                     </ul>
                     <button class="btn btn-primary-custom w-100">Выбрать план</button>
                  </div>
               </div>
               <div class="col-md-4">
                  <div class="pricing-card">
                     <div class="plan-name">Про</div>
                     <div class="plan-price">Индивидуально</div>
                     <p>Для крупных поставщиков</p>
                     <ul class="plan-features">
                        <li><i class="bi bi-check-circle-fill"></i> Все функции стандартного плана</li>
                        <li><i class="bi bi-check-circle-fill"></i> Полная FTP-интеграция</li>
                        <li><i class="bi bi-check-circle-fill"></i> Персональный менеджер</li>
                        <li><i class="bi bi-check-circle-fill"></i> API для интеграции</li>
                        <li><i class="bi bi-check-circle-fill"></i> Кастомизация под бизнес</li>
                     </ul>
                     <button class="btn btn-outline-custom w-100">Связаться с нами</button>
                  </div>
               </div>
            </div>
            <div class="text-center mt-5">
               <div class="alert alert-info d-inline-block">
                  <i class="bi bi-info-circle-fill me-2"></i>
                  Портал зарабатывает только тогда, когда зарабатываете вы! Никаких абонентских плат.
               </div>
            </div>
         </div>
      </section>
      <!-- Отзывы -->
      <section class="py-5" style="background-color: var(--light-bg);">
         <div class="container">
            <div class="text-center mb-5">
               <h2 class="section-title">Отзывы клиентов</h2>
               <p class="lead">Что говорят о нас наши пользователи</p>
            </div>
            <div class="row">
               <div class="col-md-6 col-lg-4">
                  <div class="testimonial-card">
                     <div class="testimonial-text">
                        "ХабЗа кардинально изменил наш процесс закупок. Раньше на поиск поставщиков уходило до 3 дней, теперь находим лучшие цены за 30 минут. Интеграция с 1С работает безупречно!"
                     </div>
                     <div class="client-info">
                        <div class="client-avatar">АС</div>
                        <div>
                           <div class="fw-bold">Александр Смирнов</div>
                           <div>Директор по закупкам, ООО "СтройИнвест"</div>
                        </div>
                     </div>
                  </div>
               </div>
               <div class="col-md-6 col-lg-4">
                  <div class="testimonial-card">
                     <div class="testimonial-text">
                        "Благодаря автоматической выгрузке прайсов через FTP мы экономим около 20 часов менеджерского времени в месяц. Количество новых клиентов выросло на 40% за первый квартал."
                     </div>
                     <div class="client-info">
                        <div class="client-avatar">ЕП</div>
                        <div>
                           <div class="fw-bold">Елена Петрова</div>
                           <div>Коммерческий директор, ООО "МеталлПром"</div>
                        </div>
                     </div>
                  </div>
               </div>
               <div class="col-md-6 col-lg-4">
                  <div class="testimonial-card">
                     <div class="testimonial-text">
                        "Прозрачность рынка - главное преимущество ХабЗа. Всегда знаем актуальные цены и наличие материалов. Снизили затраты на закупки на 15% за счет оптимизации поставщиков."
                     </div>
                     <div class="client-info">
                        <div class="client-avatar">ДК</div>
                        <div>
                           <div class="fw-bold">Дмитрий Кузнецов</div>
                           <div>Руководитель проекта, ЗАО "ГородСтрой"</div>
                        </div>
                     </div>
                  </div>
               </div>
            </div>
         </div>
      </section>
      <!-- Контакты -->
      <section id="contact" class="py-5">
         <div class="container">
            <div class="text-center mb-5">
               <h2 class="section-title">Свяжитесь с нами</h2>
               <p class="lead">Готовы ответить на все ваши вопросы</p>
            </div>
            <div class="row">
               <div class="col-lg-6">
                  <form>
                     <div class="row g-3">
                        <div class="col-md-6">
                           <input type="text" class="form-control" placeholder="Ваше имя">
                        </div>
                        <div class="col-md-6">
                           <input type="email" class="form-control" placeholder="Email">
                        </div>
                        <div class="col-12">
                           <input type="text" class="form-control" placeholder="Компания">
                        </div>
                        <div class="col-12">
                           <textarea class="form-control" rows="4" placeholder="Ваше сообщение"></textarea>
                        </div>
                        <div class="col-12">
                           <button type="submit" class="btn btn-primary-custom">Отправить сообщение</button>
                        </div>
                     </div>
                  </form>
               </div>
               <div class="col-lg-6">
                  <div class="ps-lg-5">
                     <h4 class="mb-4">Контактная информация</h4>
                     <div class="d-flex align-items-start mb-3">
                        <i class="bi bi-geo-alt-fill text-primary me-3" style="font-size: 1.5rem;"></i>
                        <div>
                           <h5>Адрес</h5>
                           <p>г. Москва, ул. Строительная, д. 15, офис 305</p>
                        </div>
                     </div>
                     <div class="d-flex align-items-start mb-3">
                        <i class="bi bi-telephone-fill text-primary me-3" style="font-size: 1.5rem;"></i>
                        <div>
                           <h5>Телефон</h5>
                           <p>+7 (495) 123-45-67</p>
                        </div>
                     </div>
                     <div class="d-flex align-items-start mb-3">
                        <i class="bi bi-envelope-fill text-primary me-3" style="font-size: 1.5rem;"></i>
                        <div>
                           <h5>Email</h5>
                           <p>info@hubza.ru</p>
                        </div>
                     </div>
                     <div class="d-flex align-items-start">
                        <i class="bi bi-clock-fill text-primary me-3" style="font-size: 1.5rem;"></i>
                        <div>
                           <h5>Режим работы</h5>
                           <p>Пн-Пт: 9:00 - 18:00<br>Сб-Вс: выходной</p>
                        </div>
                     </div>
                  </div>
               </div>
            </div>
         </div>
      </section>
      <!-- Футер -->
      <footer>
         <div class="container">
            <div class="row">
               <div class="col-lg-4 mb-4">
                  <div class="footer-logo">ХабЗа</div>
                  <p>Цифровой строительный портал. Прямая связь между производителями и застройщиками.</p>
                  <div class="social-icons">
                     <a href="#"><i class="bi bi-facebook"></i></a>
                     <a href="#"><i class="bi bi-twitter"></i></a>
                     <a href="#"><i class="bi bi-linkedin"></i></a>
                     <a href="#"><i class="bi bi-instagram"></i></a>
                     <a href="#"><i class="bi bi-youtube"></i></a>
                  </div>
               </div>
               <div class="col-lg-2 col-md-6 mb-4">
                  <h5 class="mb-3">Портал</h5>
                  <ul class="footer-links">
                     <li><a href="#">О проекте</a></li>
                     <li><a href="#">Возможности</a></li>
                     <li><a href="#">Интеграция 1С</a></li>
                     <li><a href="#">Тарифы</a></li>
                     <li><a href="#">Как это работает</a></li>
                  </ul>
               </div>
               <div class="col-lg-2 col-md-6 mb-4">
                  <h5 class="mb-3">Покупателям</h5>
                  <ul class="footer-links">
                     <li><a href="#">Регистрация</a></li>
                     <li><a href="#">Каталог товаров</a></li>
                     <li><a href="#">Как заказать</a></li>
                     <li><a href="#">Оплата и доставка</a></li>
                     <li><a href="#">FAQ</a></li>
                  </ul>
               </div>
               <div class="col-lg-2 col-md-6 mb-4">
                  <h5 class="mb-3">Поставщикам</h5>
                  <ul class="footer-links">
                     <li><a href="#">Стать поставщиком</a></li>
                     <li><a href="#">Интеграция с 1С</a></li>
                     <li><a href="#">Управление товарами</a></li>
                     <li><a href="#">Аналитика продаж</a></li>
                     <li><a href="#">Требования</a></li>
                  </ul>
               </div>
               <div class="col-lg-2 col-md-6 mb-4">
                  <h5 class="mb-3">Поддержка</h5>
                  <ul class="footer-links">
                     <li><a href="#">Контакты</a></li>
                     <li><a href="#">Документация</a></li>
                     <li><a href="#">API</a></li>
                     <li><a href="#">Правила портала</a></li>
                     <li><a href="#">Политика конфиденциальности</a></li>
                  </ul>
               </div>
            </div>
            <div class="copyright">
               &copy; 2023 ХабЗа. Все права защищены.
            </div>
         </div>
      </footer>
      <!-- Модальное окно загрузки документов -->
      <div class="modal fade" id="uploadModal" tabindex="-1" aria-hidden="true">
         <div class="modal-dialog modal-lg modal-dialog-centered">
            <div class="modal-content">
               <div class="modal-header">
                  <h5 class="modal-title">Загрузка проектной документации</h5>
                  <button type="button" class="btn-close btn-close-white" data-bs-dismiss="modal" aria-label="Close"></button>
               </div>
               <div class="modal-body">
                  <div class="file-upload">
                     <i class="bi bi-cloud-upload" style="font-size: 3rem; color: var(--accent-color); margin-bottom: 20px;"></i>
                     <h4>Перетащите файлы сюда</h4>
                     <p class="text-muted">или нажмите для выбора файлов</p>
                     <input type="file" class="d-none" id="fileInput" multiple accept=".pdf,.docx,.doc,.xls,.xlsx,.dwg,.dxf">
                     <button class="btn btn-primary-custom" onclick="document.getElementById('fileInput').click()">Выбрать файлы</button>
                     <div class="file-types mt-4">
                        <div class="file-type"><i class="bi bi-file-pdf"></i>PDF</div>
                        <div class="file-type"><i class="bi bi-file-word"></i>DOC/DOCX</div>
                        <div class="file-type"><i class="bi bi-file-excel"></i>XLS/XLSX</div>
                        <div class="file-type"><i class="bi bi-file-image"></i>DWG/DXF</div>
                     </div>
                  </div>
                  <div class="mt-4">
                     <h5>Что будет проанализировано:</h5>
                     <ul>
                        <li>Спецификации материалов и оборудования</li>
                        <li>Объемы работ и нормативы расхода</li>
                        <li>Технические требования и ГОСТы</li>
                        <li>График строительства и ключевые даты</li>
                        <li>Сметная документация</li>
                     </ul>
                  </div>
                  <div class="alert alert-info mt-4">
                     <i class="bi bi-info-circle-fill me-2"></i>
                     После загрузки документов система автоматически проведет анализ и предоставит рекомендации по оптимизации затрат.
                  </div>
               </div>
               <div class="modal-footer">
                  <button type="button" class="btn btn-outline-custom" data-bs-dismiss="modal">Отмена</button>
                  <button type="button" class="btn btn-primary-custom" onclick="startAnalysis()">Начать анализ</button>
               </div>
            </div>
         </div>
      </div>
      <!-- Модальное окно входа -->
      <div class="modal fade" id="loginModal" tabindex="-1" aria-hidden="true">
         <div class="modal-dialog modal-dialog-centered">
            <div class="modal-content">
               <div class="modal-header border-0">
                  <h5 class="modal-title">Вход в систему</h5>
                  <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
               </div>
               <div class="modal-body">
                  <form>
                     <div class="mb-3">
                        <label for="loginEmail" class="form-label">Email</label>
                        <input type="email" class="form-control" id="loginEmail" placeholder="name@example.com">
                     </div>
                     <div class="mb-3">
                        <label for="loginPassword" class="form-label">Пароль</label>
                        <input type="password" class="form-control" id="loginPassword" placeholder="Пароль">
                     </div>
                     <div class="mb-3 form-check">
                        <input type="checkbox" class="form-check-input" id="rememberMe">
                        <label class="form-check-label" for="rememberMe">Запомнить меня</label>
                     </div>
                     <div class="d-grid gap-2">
                        <button type="submit" class="btn btn-primary-custom">Войти</button>
                        <a href="#" class="text-center">Забыли пароль?</a>
                     </div>
                  </form>
               </div>
               <div class="modal-footer border-0">
                  <div class="text-center w-100">
                     Нет аккаунта? <a href="#" data-bs-toggle="modal" data-bs-target="#registerModal">Зарегистрироваться</a>
                  </div>
               </div>
            </div>
         </div>
      </div>
      <!-- Модальное окно регистрации -->
      <div class="modal fade" id="registerModal" tabindex="-1" aria-hidden="true">
         <div class="modal-dialog modal-dialog-centered modal-lg">
            <div class="modal-content">
               <div class="modal-header border-0">
                  <h5 class="modal-title">Регистрация</h5>
                  <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
               </div>
               <div class="modal-body">
                  <ul class="nav nav-tabs mb-4" id="registerTabs" role="tablist">
                     <li class="nav-item" role="presentation">
                        <button class="nav-link active" id="buyer-tab" data-bs-toggle="tab" data-bs-target="#buyer" type="button" role="tab">Я покупатель</button>
                     </li>
                     <li class="nav-item" role="presentation">
                        <button class="nav-link" id="supplier-tab" data-bs-toggle="tab" data-bs-target="#supplier" type="button" role="tab">Я поставщик</button>
                     </li>
                  </ul>
                  <div class="tab-content" id="registerTabsContent">
                     <div class="tab-pane fade show active" id="buyer" role="tabpanel">
                        <form>
                           <div class="row g-3">
                              <div class="col-md-6">
                                 <label class="form-label">Название компании</label>
                                 <input type="text" class="form-control" placeholder="ООО 'СтройГрад'">
                              </div>
                              <div class="col-md-6">
                                 <label class="form-label">ИНН</label>
                                 <input type="text" class="form-control" placeholder="1234567890">
                              </div>
                              <div class="col-md-6">
                                 <label class="form-label">Ваше имя</label>
                                 <input type="text" class="form-control" placeholder="Иван Иванов">
                              </div>
                              <div class="col-md-6">
                                 <label class="form-label">Должность</label>
                                 <input type="text" class="form-control" placeholder="Директор по закупкам">
                              </div>
                              <div class="col-md-6">
                                 <label class="form-label">Email</label>
                                 <input type="email" class="form-control" placeholder="name@example.com">
                              </div>
                              <div class="col-md-6">
                                 <label class="form-label">Телефон</label>
                                 <input type="tel" class="form-control" placeholder="+7 (999) 123-45-67">
                              </div>
                              <div class="col-12">
                                 <label class="form-label">Пароль</label>
                                 <input type="password" class="form-control" placeholder="Минимум 8 символов">
                              </div>
                              <div class="col-12">
                                 <div class="form-check">
                                    <input class="form-check-input" type="checkbox" id="buyerAgree">
                                    <label class="form-check-label" for="buyerAgree">
                                    Я согласен с <a href="#">условиями использования</a> и <a href="#">политикой конфиденциальности</a>
                                    </label>
                                 </div>
                              </div>
                              <div class="col-12">
                                 <button type="submit" class="btn btn-primary-custom w-100">Зарегистрироваться</button>
                              </div>
                           </div>
                        </form>
                     </div>
                     <div class="tab-pane fade" id="supplier" role="tabpanel">
                        <form>
                           <div class="row g-3">
                              <div class="col-md-6">
                                 <label class="form-label">Название компании</label>
                                 <input type="text" class="form-control" placeholder="ООО 'СтройРесурс'">
                              </div>
                              <div class="col-md-6">
                                 <label class="form-label">ИНН</label>
                                 <input type="text" class="form-control" placeholder="1234567890">
                              </div>
                              <div class="col-md-6">
                                 <label class="form-label">Ваше имя</label>
                                 <input type="text" class="form-control" placeholder="Петр Петров">
                              </div>
                              <div class="col-md-6">
                                 <label class="form-label">Должность</label>
                                 <input type="text" class="form-control" placeholder="Коммерческий директор">
                              </div>
                              <div class="col-md-6">
                                 <label class="form-label">Email</label>
                                 <input type="email" class="form-control" placeholder="name@example.com">
                              </div>
                              <div class="col-md-6">
                                 <label class="form-label">Телефон</label>
                                 <input type="tel" class="form-control" placeholder="+7 (999) 123-45-67">
                              </div>
                              <div class="col-12">
                                 <label class="form-label">Пароль</label>
                                 <input type="password" class="form-control" placeholder="Минимум 8 символов">
                              </div>
                              <div class="col-12">
                                 <label class="form-label">Тип интеграции с 1С</label>
                                 <select class="form-select">
                                    <option selected>Пока не знаю, помогите выбрать</option>
                                    <option>Ручная загрузка (Excel/CSV)</option>
                                    <option>CommerceML (стандартный)</option>
                                    <option>FTP (полная автоматизация)</option>
                                 </select>
                              </div>
                              <div class="col-12">
                                 <div class="form-check">
                                    <input class="form-check-input" type="checkbox" id="supplierAgree">
                                    <label class="form-check-label" for="supplierAgree">
                                    Я согласен с <a href="#">условиями использования</a> и <a href="#">политикой конфиденциальности</a>
                                    </label>
                                 </div>
                              </div>
                              <div class="col-12">
                                 <button type="submit" class="btn btn-primary-custom w-100">Зарегистрироваться</button>
                              </div>
                           </div>
                        </form>
                     </div>
                  </div>
               </div>
               <div class="modal-footer border-0">
                  <div class="text-center w-100">
                     Уже есть аккаунт? <a href="#" data-bs-toggle="modal" data-bs-target="#loginModal">Войти</a>
                  </div>
               </div>
            </div>
         </div>
      </div>
      <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/js/bootstrap.bundle.min.js"></script>
      <script>
         // Активация фильтров
         document.querySelectorAll('.filter-tag').forEach(tag => {
             tag.addEventListener('click', function() {
                 document.querySelectorAll('.filter-tag').forEach(t => t.classList.remove('active'));
                 this.classList.add('active');
             });
         });
         
         // Активация вкладок в личном кабинете
         document.querySelectorAll('.dashboard-tab').forEach(tab => {
             tab.addEventListener('click', function() {
                 const parent = this.closest('.dashboard-tabs');
                 parent.querySelectorAll('.dashboard-tab').forEach(t => t.classList.remove('active'));
                 this.classList.add('active');
                 
                 // Если выбрана вкладка "Аналитика проекта", показываем соответствующий раздел
                 if (this.textContent.includes('Аналитика проекта')) {
                     document.querySelector('.analytics-section').scrollIntoView({ behavior: 'smooth' });
                 }
                 
                 // Если выбрана вкладка "Поиск поставщиков", показываем соответствующий раздел
                 if (this.textContent.includes('Поиск поставщиков')) {
                     document.querySelector('.supplier-search-section').scrollIntoView({ behavior: 'smooth' });
                 }
             });
         });
         
         // Плавная прокрутка к секциям
         document.querySelectorAll('a[href^="#"]').forEach(anchor => {
             anchor.addEventListener('click', function (e) {
                 e.preventDefault();
                 const target = document.querySelector(this.getAttribute('href'));
                 if (target) {
                     window.scrollTo({
                         top: target.offsetTop - 80,
                         behavior: 'smooth'
                     });
                 }
             });
         });
         
         // Обработка форм
         document.querySelectorAll('form').forEach(form => {
             form.addEventListener('submit', function(e) {
                 e.preventDefault();
                 alert('Форма отправлена! В реальном приложении здесь будет обработка данных.');
             });
         });
         
         // Функция для симуляции анализа документов
         function startAnalysis() {
             // Закрываем модальное окно
             const uploadModal = bootstrap.Modal.getInstance(document.getElementById('uploadModal'));
             uploadModal.hide();
             
             // Показываем прогресс анализа
             document.getElementById('uploadArea').style.display = 'none';
             document.getElementById('analysisProgress').style.display = 'block';
             
             // Симулируем прогресс
             let progress = 0;
             const progressBar = document.querySelector('.progress-bar');
             const steps = ['step1', 'step2', 'step3', 'step4'];
             let currentStep = 0;
             
             const interval = setInterval(() => {
                 progress += 5;
                 progressBar.style.width = progress + '%';
                 
                 // Активируем шаги анализа
                 if (progress >= 25 && currentStep === 0) {
                     document.getElementById(steps[0]).classList.add('completed');
                     document.getElementById(steps[1]).classList.add('active');
                     currentStep = 1;
                 } else if (progress >= 50 && currentStep === 1) {
                     document.getElementById(steps[1]).classList.add('completed');
                     document.getElementById(steps[2]).classList.add('active');
                     currentStep = 2;
                 } else if (progress >= 75 && currentStep === 2) {
                     document.getElementById(steps[2]).classList.add('completed');
                     document.getElementById(steps[3]).classList.add('active');
                     currentStep = 3;
                 } else if (progress >= 100) {
                     document.getElementById(steps[3]).classList.add('completed');
                     clearInterval(interval);
                     
                     // Показываем результаты
                     setTimeout(() => {
                         document.getElementById('analysisProgress').style.display = 'none';
                         document.getElementById('resultsSection').style.display = 'block';
                         
                         // Показываем уведомление
                         showNotification('Анализ завершен! Рекомендации по поставщикам готовы.');
                     }, 1000);
                 }
             }, 200);
         }
         
         // Функция для симуляции поиска поставщиков
         function startSupplierSearch() {
             // Показываем результаты поиска
             document.getElementById('searchResults').style.display = 'block';
             
             // Показываем панель уведомлений
             showNotificationPanel();
             
             // Прокручиваем к результатам
             document.getElementById('searchResults').scrollIntoView({ behavior: 'smooth' });
             
             // Симулируем добавление уведомлений
             setTimeout(() => {
                 addNotification('high-risk', 'Высокий риск срыва сроков', 'Поставщик АО "ЦементПром" может не успеть доставить материалы к указанному сроку из-за удаленности.');
             }, 2000);
             
             setTimeout(() => {
                 addNotification('medium-risk', 'Средний риск дефицита', 'У ООО "СтройРесурс" ограниченное количество материала на складе. Рекомендуется ускорить оформление заказа.');
             }, 4000);
             
             setTimeout(() => {
                 addNotification('success', 'Оптимальный поставщик найден', 'ООО "МеталлТрейд" соответствует всем требованиям проекта. Рекомендуется к сотрудничеству.');
             }, 6000);
         }
         
         // Функция для анализа участка
         function analyzePlot() {
             const cadastralNumber = document.getElementById('cadastralNumber').value;
             
             if (!cadastralNumber) {
                 showNotification('Пожалуйста, введите кадастровый номер участка');
                 return;
             }
             
             // Показываем индикатор загрузки
             showNotification('Выполняется анализ участка...');
             
             // Симулируем задержку анализа
             setTimeout(() => {
                 // Показываем результаты
                 document.getElementById('assistantResults').style.display = 'block';
                 
                 // Прокручиваем к результатам
                 document.getElementById('assistantResults').scrollIntoView({ behavior: 'smooth' });
                 
                 // Показываем уведомление о завершении
                 showNotification('Анализ завершен! Результаты готовы.');
                 
                 // Добавляем уведомление о рисках
                 setTimeout(() => {
                     addNotification('high-risk', 'Обнаружено ограничение', 'Участок частично попадает в санитарно-защитную зону промышленного предприятия.');
                 }, 2000);
             }, 2000);
         }
         
         // Функция для показа выбора на карте
         function showMapSelector() {
             const mapSelector = document.getElementById('mapSelector');
             mapSelector.style.display = mapSelector.style.display === 'none' ? 'block' : 'none';
         }
         
         // Функция для показа уведомлений
         function showNotification(message) {
             const notification = document.createElement('div');
             notification.className = 'alert alert-success alert-dismissible fade show position-fixed';
             notification.style.cssText = 'top: 20px; right: 20px; z-index: 9999; min-width: 300px;';
             notification.innerHTML = `
                 ${message}
                 <button type="button" class="btn-close" data-bs-dismiss="alert"></button>
             `;
             document.body.appendChild(notification);
             
             // Автоматически скрываем через 5 секунд
             setTimeout(() => {
                 notification.remove();
             }, 5000);
         }
         
         // Функция для показа панели уведомлений
         function showNotificationPanel() {
             const panel = document.getElementById('notificationPanel');
             panel.style.display = 'block';
             
             // Автоматически скрываем через 30 секунд
             setTimeout(() => {
                 panel.style.display = 'none';
             }, 30000);
         }
         
         // Функция для закрытия панели уведомлений
         function closeNotifications() {
             document.getElementById('notificationPanel').style.display = 'none';
         }
         
         // Функция для добавления уведомления в панель
         function addNotification(type, title, message) {
             const notificationList = document.getElementById('notificationList');
             const notification = document.createElement('div');
             notification.className = `notification-item ${type}`;
             notification.innerHTML = `
                 <div class="d-flex justify-content-between align-items-start">
                     <div>
                         <strong>${title}</strong>
                         <div>${message}</div>
                         <div class="notification-time">Только что</div>
                     </div>
                 </div>
             `;
             
             // Добавляем в начало списка
             notificationList.insertBefore(notification, notificationList.firstChild);
             
             // Ограничиваем количество уведомлений
             if (notificationList.children.length > 5) {
                 notificationList.removeChild(notificationList.lastChild);
             }
         }
         
         // Обработка кнопок "Найти поставщиков"
         document.querySelectorAll('.btn-outline-custom').forEach(btn => {
             if (btn.textContent === 'Найти поставщиков') {
                 btn.addEventListener('click', function() {
                     showNotification('Подбор поставщиков для данного материала...');
                     
                     // Симулируем задержку и показываем результат
                     setTimeout(() => {
                         document.querySelector('.supplier-search-section').scrollIntoView({ behavior: 'smooth' });
                         showNotification('Найдены 4 оптимальных поставщика!');
                     }, 1500);
                 });
             }
         });
         
         // Обработка кнопок "Отправить запрос"
         document.querySelectorAll('.btn-request').forEach(btn => {
             btn.addEventListener('click', function() {
                 const supplierName = this.closest('.supplier-card, .supplier-match-card').querySelector('.supplier-name').textContent;
                 showNotification(`Запрос отправлен поставщику: ${supplierName}`);
                 
                 // Симулируем уведомление для поставщика
                 setTimeout(() => {
                     showNotification('Поставщик получил уведомление о вашем запросе!');
                 }, 2000);
             });
         });
         
         // Обработка кнопок "Связаться"
         document.querySelectorAll('.btn-contact').forEach(btn => {
             btn.addEventListener('click', function() {
                 const supplierName = this.closest('.supplier-card, .supplier-match-card').querySelector('.supplier-name').textContent;
                 alert(`Контактная информация поставщика ${supplierName}:\n\nТелефон: +7 (XXX) XXX-XX-XX\nEmail: contact@supplier.ru`);
             });
         });
         
         // Обработка оптимизационных карточек
         document.querySelectorAll('.optimization-card').forEach(card => {
             card.addEventListener('click', function() {
                 document.querySelectorAll('.optimization-card').forEach(c => c.classList.remove('selected'));
                 this.classList.add('selected');
                 
                 const optimizationType = this.dataset.opt;
                 showNotification(`Выбран тип оптимизации: ${this.querySelector('.optimization-title').textContent}`);
             });
         });
         
         // Drag and drop для загрузки файлов
         const uploadArea = document.getElementById('uploadArea');
         
         uploadArea.addEventListener('dragover', (e) => {
             e.preventDefault();
             uploadArea.style.backgroundColor = 'rgba(44, 122, 123, 0.1)';
         });
         
         uploadArea.addEventListener('dragleave', () => {
             uploadArea.style.backgroundColor = 'rgba(44, 122, 123, 0.05)';
         });
         
         uploadArea.addEventListener('drop', (e) => {
             e.preventDefault();
             uploadArea.style.backgroundColor = 'rgba(44, 122, 123, 0.05)';
             
             const files = e.dataTransfer.files;
             if (files.length > 0) {
                 showNotification(`Загружено файлов: ${files.length}`);
                 // Здесь была бы обработка файлов
             }
         });
      </script>
   </body>
</html>
