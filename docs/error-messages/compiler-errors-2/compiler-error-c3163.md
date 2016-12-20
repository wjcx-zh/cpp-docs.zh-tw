---
title: "編譯器錯誤 C3163 | Microsoft Docs"
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
  - "C3163"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3163"
ms.assetid: 17dcafa3-f416-4e04-a232-f9569218ba75
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3163
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'construct' : 屬性與先前宣告不一致  
  
 套用至定義的屬性與套用至宣告的屬性衝突。  
  
 解決 C3163 的其中一種方式是排除向前宣告的屬性。  向前宣告的任何屬性都應該小於 \(或至多等於\) 定義的屬性。  
  
 C3163 錯誤可能的原因牽扯到原始程式碼附註語言 \(SAL\)。  除非您使用 **\/analyze** 旗標編譯專案，否則 SAL 巨集不會擴展。  如果您嘗試使用 \/analyze 選項進行編譯，不使用 \/analyze 清楚編譯的程式可能會擲回 C3163。  如需 SAL 的詳細資訊，請參閱 [SAL 註釋](../../c-runtime-library/sal-annotations.md)。  
  
## 範例  
 下列範例會產生 C3163。  
  
```  
// C3163.cpp  
// compile with: /clr /c  
using namespace System;  
  
[CLSCompliant(true)] void f();  
[CLSCompliant(false)] void f() {}   // C3163  
// try the following line instead  
// [CLSCompliant(true)] void f() {}  
```  
  
## 請參閱  
 [SAL 註釋](../../c-runtime-library/sal-annotations.md)