---
title: "編譯器警告 (層級 3) C4580 | Microsoft Docs"
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
  - "C4580"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4580"
ms.assetid: fef6e8e0-0d6a-44fa-b22a-2fe7ba2ef379
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 3) C4580
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

\[attribute\] 已被取代；請改為指定 System::Attribute 或 Platform::Metadata 作為基底類別  
  
 [attribute](../../windows/attribute.md)已不再是建立使用者定義屬性的慣用語法。  如需詳細資訊，請參閱[User\-Defined Attributes](../../windows/user-defined-attributes-cpp-component-extensions.md)。  針對 CLR 程式碼，請從 [System::Attribute](assetId:///System::Attribute?qualifyHint=False&autoUpgrade=True) 衍生屬性。  針對 Windows 執行階段程式碼，請從 `Platform::Metadata` 衍生屬性。  
  
## 範例  
 下列範例會產生 C3454，並說明如何加以修正。  
  
```  
// C4580.cpp  
// compile with: /W3 /c /clr  
[attribute]   // C4580  
public ref class Attr {  
public:  
   int m_t;  
};  
  
public ref class Attr2 : System::Attribute {  
public:  
   int m_t;  
};  
```