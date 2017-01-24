---
title: "使用偵錯版檢查記憶體覆寫 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "記憶體, 覆寫"
ms.assetid: 1345eb4d-24ba-4595-b1cc-2da66986311e
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 使用偵錯版檢查記憶體覆寫
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

若要使用偵錯版來檢查記憶體覆寫，您必須先重新建置專案以進行偵錯。  然後，移至應用程式的 `InitInstance` 函式的最前面，並加入下面這一行：  
  
```  
afxMemDF |= checkAlwaysMemDF;  
```  
  
 偵錯記憶體配置器會在所有記憶體配置周圍放置保護位元組。  不過，除非您檢查這些保護位元組是否已變更 \(其會指示記憶體覆寫\)，否則它們並沒有任何效用。  不然，這事實上只是提供一個能讓您消除記憶體覆寫的緩衝區而已。  
  
 在開啟 `checkAlwaysMemDF` 後，您將強制 MFC 在每次呼叫 **new** 或 **delete** 時，呼叫 `AfxCheckMemory` 函式。  如果偵測到記憶體覆寫，它將會產生一則類似下列的 TRACE 訊息：  
  
```  
Damage Occurred! Block=0x5533  
```  
  
 如果看到這其中一則訊息，您必須逐步執行程式碼以判斷何處發生損毀。  若要更確切地找出發生記憶體覆寫的位置，您可自行明確呼叫 `AfxCheckMemory`。  例如：  
  
```  
ASSERT(AfxCheckMemory());  
    DoABunchOfStuff();  
    ASSERT(AfxCheckMemory());  
```  
  
 如果第一個 ASSERT 成功，而第二個失敗，則表示兩個呼叫之間的函式中必定發生了記憶體覆寫。  
  
 依據您應用程式的本質，您可能發現 `afxMemDF` 導致您的程式執行過慢，而無法通過測試。  `afxMemDF` 變數會造成在每次呼叫 new 和 delete 時，呼叫 `AfxCheckMemory`。  在該情況下，您應如上所示散佈您自己對 `AfxCheckMemory`\( \) 的呼叫，然後嘗試以該方式隔離記憶體覆寫。  
  
## 請參閱  
 [解決發行組建的問題](../../build/reference/fixing-release-build-problems.md)