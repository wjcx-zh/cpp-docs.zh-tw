---
title: "有任何 MFC 類別或函式不能用於 MFC DLL 嗎？ | Microsoft Docs"
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
  - "DLL [C++], MFC"
  - "DLL [C++], 限制"
  - "MFC DLL [C++], 限制"
ms.assetid: 18e2f1cb-4f72-4d3a-a951-3488208872c7
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 有任何 MFC 類別或函式不能用於 MFC DLL 嗎？
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

擴充 DLL 使用用戶端應用程式的 `CWinApp` 衍生類別。  它們不能有自己的 `CWinApp` 衍生類別。  
  
 標準 DLL 必須像 MFC 應用程式一樣，擁有 `CWinApp` 衍生類別和此應用程式類別的單一物件。  不同於應用程式的 `CWinApp` 物件，DLL 的 `CWinApp` 物件沒有主要的訊息幫浦。  
  
 請注意，應用程式有自己的主要訊息幫浦，所以 `CWinApp::Run` 機制並不適用於 DLL。  如果 DLL 開啟非強制回應的對話方塊，或是擁有自己的主框架視窗 \(Main Frame Window\)，應用程式的主要訊息幫浦就必須呼叫由 DLL 匯出的常式，該常式會接著呼叫 DLL 應用程式物件的 `CWinApp::PreTranslateMessage` 成員函式。  
  
## 請參閱  
 [DLL 常見問題集](../build/dll-frequently-asked-questions.md)