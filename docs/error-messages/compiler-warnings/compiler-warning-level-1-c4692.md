---
title: "編譯器警告 (層級 1) C4692 | Microsoft Docs"
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
  - "C4692"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4692"
ms.assetid: f6fb3acc-8228-491a-9c30-ce302d8a9c75
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1) C4692
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'function': 非私用成員的簽章含有組件私用原生類型 'native\_type'  
  
 可以在組件之外看見的型別，含有其簽章中包含在組件之外不可見之原生型別的成員函式。  因此，如果包含其中的型別是在組件之外具現化，就不應該呼叫成員函式。  
  
 如需詳細資訊，請參閱[類型可視性](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Type_visibility)。  
  
 此警告在預設情況下為關閉的。  如需詳細資訊，請參閱[預設為關閉的編譯器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md)。  
  
## 範例  
 下列範例會產生 C4692。  
  
```  
// C4692.cpp  
// compile with: /W1 /c /clr  
#pragma warning(default:4692)  
class Private_Native_Class {};  
public class Public_Native_Class {};  
public ref class Public_Ref_Class {  
public:  
   void Test(Private_Native_Class *) {}   // C4692  
   void Test2(Public_Native_Class *) {}   // OK  
};  
```