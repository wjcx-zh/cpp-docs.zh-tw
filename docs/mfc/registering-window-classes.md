---
title: "註冊視窗類別 | Microsoft Docs"
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
  - "WndProc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AfxRegisterWndClass 方法"
  - "類別 [C++], 註冊視窗類別"
  - "MFC, 視窗"
  - "註冊視窗類別"
  - "登錄, 註冊類別"
  - "視窗類別, 註冊"
  - "WinMain 方法"
  - "WinMain 方法, 和註冊視窗類別"
  - "WndProc 方法"
ms.assetid: 30994bc4-a362-43da-bcc5-1bf67a3fc929
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 註冊視窗類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Window 在「視窗」的傳統程式設計中分類定義「類別」的特性 \(不是 C \+\+ 類別\) 任何數目的視窗中建立。  這個類別是一個樣板或模型建立的視窗。  
  
## 視窗在傳統程式的類別註冊視窗  
 在視窗中的傳統的程式，而非 MFC，您會處理所有訊息到其「視窗程序」或「**WndProc**」的視窗。**WndProc** 與視窗將「視窗類別註冊」流程。  主視窗在 `WinMain` 函式中註冊，但視窗其他類別包含在應用程式可以註冊。  註冊取決於包含指標 **WndProc** 函式與游標，背景筆刷的規格，一起等等的結構。  結構會當做參數傳遞，與類別的字串名稱以外，在之前的呼叫 **RegisterClass** 函式。  因此，註冊類別可由多個視窗共用。  
  
## 視窗在 MFC 程式的類別註冊  
 相反地，大部分視窗類別註冊活動在 MFC 架構計劃就會自動完成。  如果您使用 MFC，使用類別繼承，一般 C\+\+ 語法您從現有程式庫通常衍生自類別 C \+\+. 視窗類別。  架構仍然使用傳統登入類別，並為您提供數個標準區段登錄。  您可以藉由呼叫 [AfxRegisterWndClass](../Topic/AfxRegisterWndClass.md) 全域函式會註冊類別註冊其他註冊類別對 `CWnd`**Create** 的成員函式。  如所述，傳統登入類別視窗不會與 C \+\+ 類別混淆。  
  
 如需詳細資訊，請參閱 [技術提示 1](../mfc/tn001-window-class-registration.md)。  
  
## 請參閱  
 [建立視窗](../mfc/creating-windows.md)