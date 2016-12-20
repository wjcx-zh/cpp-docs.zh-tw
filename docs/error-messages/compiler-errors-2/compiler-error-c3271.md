---
title: "編譯器錯誤 C3271 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3271"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3271"
ms.assetid: 16d8bd1d-2e30-4c6a-a07f-0c4f3342fab5
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3271
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'member': 對 FieldOffset 屬性無效的值 'value'  
  
 已傳遞負值給 [FieldOffset](frlrfSystemRuntimeInteropServicesFieldOffsetAttributeClassTopic) 屬性。  
  
 下列範例會產生 C3271：  
  
```  
// C3271.cpp // compile with: /clr /c using namespace System; using namespace System::Runtime::InteropServices; [StructLayout(LayoutKind::Explicit)] value class MyStruct1 { public: [FieldOffset(0)] int a; public: [FieldOffset(-1)] long b;   // C3271 };  
```  
  
 下列範例會產生 C3271：  
  
```  
// C3271_2.cpp // compile with: /clr:oldSyntax using namespace System; using namespace System::Runtime::InteropServices; [StructLayout(LayoutKind::Explicit)] __value class MyStruct1 { public: [FieldOffset(0)] int a; public: [FieldOffset(-1)] long b;   // C3271 }; static int main() { MyStruct1* a = __nogc new MyStruct1(); };  
```