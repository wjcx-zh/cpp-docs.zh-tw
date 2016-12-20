---
title: "DLL 中的 Automation | Microsoft Docs"
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
  - "Automation [C++], DLL"
  - "DLL [C++], Automation"
ms.assetid: 2728ecd1-14e2-4ae0-a946-e749e11dbb74
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# DLL 中的 Automation
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

這個精靈會在 MFC DLL 精靈裡選擇 \[Automation\] 選項時提供下列項目：  
  
-   起始的物件描述語言檔案 \(Object Description Language File，.ODL\)  
  
-   Afxole.h 在 STDAFX.h 檔裡的 Include 指示詞  
  
-   `DllGetClassObject` 函式的實作，它會呼叫 **AfxDllGetClassObject** 函式  
  
-   `DllCanUnloadNow` 函式的實作，它會呼叫 **AfxDllCanUnloadNow** 函式  
  
-   `DllRegisterServer` 函式的實作，它會呼叫 [COleObjectFactory::UpdateRegistryAll](../Topic/COleObjectFactory::UpdateRegistryAll.md) 函式  
  
## 您還想知道關於哪些方面的詳細資訊？  
  
-   [Automation 伺服程式](../mfc/automation-servers.md)  
  
## 請參閱  
 [Visual C\+\+ 中的 DLL](../build/dlls-in-visual-cpp.md)