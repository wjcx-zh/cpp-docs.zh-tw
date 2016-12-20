---
title: "繼承關鍵字 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "__multiple_inheritance"
  - "__single_inheritance_cpp"
  - "__virtual_inheritance_cpp"
  - "__virtual_inheritance"
  - "__multiple_inheritance_cpp"
  - "__single_inheritance"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__multiple_inheritance 關鍵字 [C++]"
  - "__single_inheritance 關鍵字 [C++]"
  - "__virtual_inheritance 關鍵字 [C++]"
  - "宣告衍生類別"
  - "衍生類別, 宣告"
  - "繼承, 宣告衍生類別"
  - "繼承, 關鍵字"
  - "關鍵字 [C++], 繼承關鍵字"
ms.assetid: bb810f56-7720-4fea-b8b6-9499edd141df
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 繼承關鍵字
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 特定的**  
  
```  
  
class [__single_inheritance] class-name; class [__multiple_inheritance] class-name; class [__virtual_inheritance] class-name;  
```  
  
 其中：  
  
 *class\-name*  
 所要宣告類別的名稱。  
  
 C\+\+ 可讓您在定義類別之前宣告類別成員的指標。  例如：  
  
```  
class S;  
int S::*p;  
```  
  
 在上述程式碼中，`p` 會宣告為類別 S 的整數成員指標。  不過，`class S` 尚未在這個程式碼中定義，僅宣告而已。  當編譯器遇到這類指標時，必須將指標的表示法一般化。  表示法的大小取決於指定的繼承模型。  有四種方式可將繼承模型指定至編譯器：  
  
-   在 IDE 中的 \[**成員指標表示法**\] 底下  
  
-   在命令列中使用 [\/vmg](../build/reference/vmb-vmg-representation-method.md) 參數  
  
-   使用 [pointers\_to\_members](../preprocessor/pointers-to-members.md) pragma  
  
-   使用繼承關鍵字 `__single_inheritance`、`__multiple_inheritance` 和 `__virtual_inheritance`。  這項技術能夠以每個類別為基礎控制繼承模型。  
  
    > [!NOTE]
    >  如果您總是在定義類別之後宣告類別成員的指標，就不需要使用上述任何選項。  
  
 在類別定義之前宣告類別成員的指標，會影響所產生可執行檔的大小和速度。  類別使用的繼承越複雜，用來表示類別成員指標所需的位元組數目就越多，而且用來解譯指標的程式碼也會越大。  單一繼承最不複雜，而虛擬繼承最為複雜。  
  
 如果上述範例變更為：  
  
```  
class __single_inheritance S;  
int S::*p;  
```  
  
 無論命令列選項或 pragma 為何，`class S` 成員的指標都會盡可能使用最小的表示法。  
  
> [!NOTE]
>  類別成員指標表示法的同一個向前宣告應出現在宣告該類別成員指標的每一個轉譯單位中，而且宣告應在成員指標宣告之前發生。  
  
 **END Microsoft 特定的**  
  
## 請參閱  
 [C\+\+ 關鍵字](../cpp/keywords-cpp.md)