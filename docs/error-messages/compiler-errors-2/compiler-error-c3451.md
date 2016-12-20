---
title: "編譯器錯誤 C3451 | Microsoft Docs"
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
  - "C3451"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3451"
ms.assetid: a4897a69-e3e7-40bb-bb1c-598644904012
caps.latest.revision: 13
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3451
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'attribute': 無法將 Unmanaged 屬性套用至 'type'  
  
 C\+\+ 屬性無法套用至 CLR 型別。  如需詳細資訊，請參閱[C\+\+ Attributes Reference](../../windows/cpp-attributes-reference.md)。  
  
 如需詳細資訊，請參閱[User\-Defined Attributes](../../windows/user-defined-attributes-cpp-component-extensions.md)。  
  
 對 Visual C\+\+ 2005 的編譯器完成一致性處理後可能會發生這項錯誤：在使用 CLR 程式設計的使用者定義屬性上不再允許 [uuid](../../windows/uuid-cpp-attributes.md) 屬性。  請改用 <xref:System.Runtime.InteropServices.GuidAttribute>。  
  
## 範例  
 下列範例會產生 C3451。  
  
```  
// C3451.cpp  
// compile with: /clr /c  
using namespace System;  
[ attribute(AttributeTargets::All) ]  
public ref struct MyAttr {};  
  
[ MyAttr, helpstring("test") ]   // C3451  
// try the following line instead  
// [ MyAttr ]  
public ref struct ABC {};  
```