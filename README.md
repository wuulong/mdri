# mdri
MDRI (Mata'an Disaster Recovery Initiative) - 馬太鞍災害復原倡議

## 專案概述
BMad Master Orchestrator 是一個用於工作流程協調、多代理任務、角色切換指導的工具，並在不確定諮詢哪個專家時提供指引。它作為 BMad 方法的專家和主協調者，提供統一的介面來管理所有 BMad-Method 的功能，並能動態轉換為任何專業代理。

## 系統架構設計重點

- [architecture_document.md](kb/architecture_document.md)
- 本系統旨在建立一個高效、透明的民間自主災害協作與智能媒合系統。其主要架構設計考量如下：

### 主要模組與組件
*   **核心數據層：** 集中儲存所有災情、需求、供給、志工等數據。
*   **應用服務層：** 處理業務邏輯，包括數據接收、處理、儲存、查詢及媒合邏輯。
*   **AI Agent 模組：** 執行智能媒合、數據分析、預測等任務。
*   **使用者介面層：** 提供 Discord Bot 和 Web/App 介面。
*   **外部系統整合層：** 透過 OpenAPI 格式的 API 與其他系統互動。
*   **ATAK 整合模組：** 負責系統與 ATAK 之間的資訊橋接，運用 TakSwak 專案實現互動。

### 技術選型考量 (以最簡單技術，快速建立為原則)
*   **後端：** Python (FastAPI/Django) 或 Node.js (Express)。
*   **資料庫：** PostgreSQL 或 MySQL。
*   **前端：** React 或 Vue.js。
*   **地圖服務：** Google Maps API 或 OpenStreetMap。
*   **AI/ML：** 初期以規則邏輯或雲端 NLP API 為主。
*   **部署：** 雲端平台 (AWS, Google Cloud, Azure)。
*   **通訊整合：** Discord API。

## 目錄結構
```
/Volumes/D2024/github/mdri/
├───.gitignore
├───LICENSE
├───README.md
├───.bmad-mdri/
│   ├───config.yaml
│   ├───install-manifest.yaml
│   ├───README.md
│   ├───agent-teams/
│   │   ├───all-response-team.yaml
│   │   └───initial-response-team.yaml
│   ├───agents/
│   │   ├───ai_matcher.md
│   │   ├───bmad-orchestrator.md
│   │   ├───data_collector.md
│   │   ├───demand_publisher.md
│   │   ├───information_reporter.md
│   │   ├───information_verifier.md
│   │   ├───logistics_support.md
│   │   ├───matching_coordinator.md
│   │   ├───software_engineer.md
│   │   ├───spokesperson.md
│   │   └───supply_provider.md
│   ├───checklists/
│   │   └───disaster-report-checklist.md
│   ├───data/
│   │   ├───bmad-kb.md
│   │   ├───disaster-relief-regulations.md
│   │   ├───elicitation-methods.md
│   │   ├───mataan-incident-background.md
│   │   └───mataan-river-geography.md
│   ├───tasks/
│   │   ├───advanced-elicitation.md
│   │   ├───create-doc.md
│   │   ├───execute-checklist.md
│   │   ├───initial-disaster-report.md
│   │   └───kb-mode-interaction.md
│   ├───templates/
│   │   ├───ai_matching_suggestion_tmpl.yaml
│   │   ├───disaster_report_tmpl.yaml
│   │   ├───press_release_tmpl.yaml
│   │   ├───shelter_demand_tmpl.yaml
│   │   ├───supply_offer_tmpl.yaml
│   │   └───transport_task_assignment_tmpl.yaml
│   ├───utils/
│   │   ├───bmad-doc-template.md
│   │   └───workflow-management.md
│   └───workflows/
│       └───disaster-handling-workflow.yaml
├───.claude/
│   └───commands/
│       ├───.bmad-mdri/
│       │   ├───agents/
│       │   │   ├───ai_matcher.md
│       │   │   ├───bmad-orchestrator.md
│       │   │   ├───data_collector.md
│       │   │   ├───demand_publisher.md
│       │   │   ├───information_reporter.md
│       │   │   ├───information_verifier.md
│       │   │   ├───logistics_support.md
│       │   │   ├───matching_coordinator.md
│       │   │   ├───software_engineer.md
│       │   │   ├───spokesperson.md
│       │   │   └───supply_provider.md
│       │   └───tasks/
│       │       ├───advanced-elicitation.md
│       │       ├───create-doc.md
│       │       ├───execute-checklist.md
│       │       ├───initial-disaster-report.md
│       │       └───kb-mode-interaction.md
│       └───BMad/
│           ├───agents/
│           └───tasks/
├───.gemini/
│   └───bmad-method/
│       └───GEMINI.md
├───.git/...
├───data/
├───kb/
│   ├───設計救災指揮體系方法.md
│   ├───agent_definitions.md
│   ├───architecture_document.md
│   ├───TakSwak.md
│   └───news/
│       ├───馬太鞍潰壩事件時間表.md
│       └───馬太鞍潰壩事件救災體系說明.md
└───tmp/
```

## 可用的專業代理 (Available Specialist Agents)

*   **AI 媒合 Agent (`ai-matcher`)**: 利用智能演算法，根據所有可用的災情、需求、供給、志工資訊，提供最佳的媒合建議、排序和路徑推薦。
*   **BMad Master Orchestrator (`bmad-orchestrator`)**: 用於工作流程協調、多代理任務、角色切換指導，並在不確定諮詢哪個專家時提供指引。
*   **資料收集 Agent (`data-collector`)**: 廣泛收集網路上可以收集到的資料，並善用政府開放資料，開放 API，持續掌握官方資訊。
*   **需求發布者 (`demand-publisher`)**: 用於清晰、完整地發布物資、人力、機具、專業服務等需求。
*   **現場災情回報者 (`information-reporter`)**: 用於即時回報馬太鞍事件現場的災情、路況、受困資訊等。
*   **資訊守門員 (`information-verifier`)**: 用於核實資訊的真實性、準確性與有效性，避免假消息或重複資訊干擾救災。
*   **救援後勤執行者 (`logistics-support`)**: 負責將媒合成功的物資從供給點運輸到需求點，並確保志工的食宿、安全等後勤保障。
*   **資源調度指揮官 (`matching-coordinator`)**: 負責人工確認 AI 媒合建議、調整任務優先級、重新分配資源，並處理複雜的媒合情境。
*   **系統建構者 (`software-engineer`)**: 可以設計與開發程式，掌握軟體專案。
*   **對外溝通介面 (`spokesperson`)**: 負責與外部的溝通介面。
*   **資源提供者 (`supply-provider`)**: 用於發布可提供的物資、人力（志工專長）、機具、專業服務等資源。

## 可用的工作流程 (Available Workflows)

*   **災情處理流程 (`disaster-handling-workflow`)**: 從災情初步回報到媒合協調的標準處理流程。