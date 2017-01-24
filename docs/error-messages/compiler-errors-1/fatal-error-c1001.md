---
title: "嚴重錯誤 C1001 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C1001"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1001"
ms.assetid: 5736cdb3-22c8-4fad-aa85-d5e0d2b232f4
caps.latest.revision: 15
caps.handback.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 嚴重錯誤 C1001
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

編譯器內部錯誤 \(編譯檔案 file，第 number 行\)  
  
 編譯器無法產生正確的建構程式碼，可能起因於運算式和最佳化選項的組合。  請嘗試移除一個或多個最佳化選項，並重新編譯包含錯誤訊息所指定行號的函式。  
  
 移除一個或多個最佳化選項可能可以修正此問題。  若要判斷導致錯誤的選項，請一次移除一個選項，並重新編譯，直到該錯誤訊息消失。  最可能導致問題的選項為 **\/Og**、**\/Oi** 和 `/Oa`。  您可以在判斷出哪個選項造成錯誤之後，在發生錯誤的函式中使用 [optimize](../../preprocessor/optimize.md) pragma 來停用該選項，並在模組的其他部分繼續使用該選項。  
  
 Microsoft知識基本庫含有關 C1001 的詳細資訊，請參閱 [http:\/\/support.microsoft.com\/default.aspx?scid\=kb;en\-us;134650](http://support.microsoft.com/default.aspx?scid=kb;en-us;134650)。  
  
 嘗試重新撰寫發生錯誤的程式行，或該行附近的幾行程式碼。