---
title: "ATL 服務 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CServiceModule"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL 服務"
  - "COM 物件, ATL"
  - "CServiceModule 類別"
  - "服務, ATL"
ms.assetid: 8c09d1a8-7548-4d2c-947c-9d795a81659b
caps.latest.revision: 12
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ATL 服務
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

建立 ATL COM 物件，讓它在服務中執行，只要選取的服務 \(EXE\) 在 ATL 專案精靈的伺服器選項清單。  精靈會建立 `CAtlServiceModuleT` 從衍生的類別會實作服務。  
  
 在 ATL COM 物件會建立做為服務啟動時，它才會登錄為本機伺服器，，而且不會出現在 \[控制台\] 中的服務清單。  這是因為，偵錯服務做為本機伺服器來當做服務會比較容易。  若要安裝為服務，請在命令提示字元中執行下列命令:  
  
 `YourEXE` `.exe /Service`  
  
 若要解除安裝此元件，請執行下列事項:  
  
 `YourEXE` `.exe /UnregServer`  
  
 本節中的前四個主題討論 `CAtlServiceModuleT` 成員函式執行時發生的動作。  這些主題會顯示在與相同的函式通常會呼叫的序列。  若要改善這些主題的關係，比較好的方式是使用 ATL 專案精靈產生的原始程式碼做為參考。  這前四個主題包括:  
  
-   [CAtlServiceModuleT::Start 函式](../atl/catlservicemodulet-start-function.md)  
  
-   [CAtlServiceModuleT::ServiceMain 函式](../atl/catlservicemodulet-servicemain-function.md)  
  
-   [CAtlServiceModuleT::Run 函式](../atl/catlservicemodulet-run-function.md)  
  
-   [CAtlServiceModuleT::Handler 函式](../atl/catlservicemodulet-handler-function.md)  
  
 前三個主題所討論的概念與開發服務相關:  
  
-   ATL 服務的[登錄項目](../atl/registry-entries.md)  
  
-   [DCOMCNFG](../atl/dcomcnfg.md)  
  
-   ATL 服務的[偵錯秘訣](../atl/debugging-tips.md)  
  
## 請參閱  
 [概念](../atl/active-template-library-atl-concepts.md)