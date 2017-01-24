---
title: "編譯器警告 (層級 4) C4820 | Microsoft Docs"
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
  - "C4820"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4820"
ms.assetid: 17aa29f4-c287-49b8-bc43-8ed82ffed5ea
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 4) C4820
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在成員建構 'member\_name' 之後加入 'bytes' 位元組填補  
  
 元素的型別與順序使編譯器在結構的結尾加入填補。  如需關於在結構中加入填補的詳細資訊，請參閱[align](../../cpp/align-cpp.md)。  
  
 此警告在預設情況下為關閉的。  如需詳細資訊，請參閱[預設為關閉的編譯器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md)。  
  
 下列範例會產生 C4820：  
  
```  
// C4820.cpp  
// compile with: /W4 /c  
#pragma warning(default : 4820)   
  
// Delete the following 4 lines to resolve.  
__declspec(align(2)) struct MyStruct {  
   char a;  
   int i;   // C4820  
};  
  
// OK  
#pragma pack(1)  
__declspec(align(1)) struct MyStruct2 {  
   char a;  
   int i;  
};  
```