---
title: "Understanding Backus Nauer Form (BNF) Syntax | Microsoft Docs"
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
  - "Backus Nauer Form (BNF) syntax"
  - "BNF notation"
ms.assetid: 994bbef0-9077-4aa8-bdfe-b7e830af9acc
caps.latest.revision: 15
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Understanding Backus Nauer Form (BNF) Syntax
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使用 BNF 文法， ATL 管理員使用的指令碼會在本主題中所述，使用下表中所示的附註。  
  
|慣例\/符號|意義|  
|------------|--------|  
|`::=`|對等用法|  
|`&#124;`|OR|  
|`X+`|一或多個 `X`s。|  
|`[X]`|`X` 是選擇性的。  任意符號由 `[]`運算式。|  
|任何 **bold** 文字|字串常值 \(String Literal\)。|  
|任何使用斜體文字|如何建構字串常值 \(String Literal\)。|  
  
 如上表所示，登錄器指令碼使用字串常值 \(String Literal\)。  這些值是必須出現在您的指令碼的實際文字。  下表說明 ATL 登錄器指令碼的字串常值 \(String Literal\)。  
  
|字串常值|動作|  
|----------|--------|  
|**ForceRemove**|完全移除的索引鍵 \(如果存在\) 再重新建立。|  
|**NoRemove**|在移除註冊期間，不會移除的索引鍵。|  
|**val**|指定 `_<Key Name_>` 實際上是具名值。|  
|**Delete**|在註冊期間，刪除下的機碼。|  
|**s**|指定下一個值為字串 \(**REG\_SZ**\)。|  
|**d**|指定的值為 **DWORD** \(**REG\_DWORD**\)。|  
|**m**|指定的值為 multistring \(**REG\_MULTI\_SZ**\)。|  
|**b**|指定下一個值為二進位值 \(**REG\_BINARY**\)。|  
  
## BNF 語法範例  
 這可以協助您進行一些語法範例了解附註和字串常值 \(String Literal\) 如何在 ATL 登錄器指令碼運作。  
  
### 語法範例 1  
  
```  
<registry expression> ::= <Add Key>  
```  
  
 指定 `registry expression` 與 `Add Key`相當於。  
  
### 語法範例 2  
  
```  
<registry expression> ::= <Add Key> | <Delete Key>  
```  
  
 指定 `registry expression` 與 `Add Key` 或 `Delete Key`相當於。  
  
### 語法範例 3  
  
```  
<Key Name> ::= '<AlphaNumeric>+'  
```  
  
 指定 `Key Name` 與一或多個 `AlphaNumerics`相當於。  
  
### 語法範例 4  
  
```  
<Add Key> ::= [ForceRemove | NoRemove | val]<Key Name>  
```  
  
 指定 `Add Key` 與 `Key Name`相等，然後，字串常值 \(String Literal\)， `ForceRemove`、 `NoRemove`和 `val`，是選擇性的。  
  
### 語法範例 5  
  
```  
<AlphaNumeric> ::= any character not NULL, that is, ASCII 0  
```  
  
 指定 `AlphaNumeric` 與任何非 null 的字元是一樣的。  
  
### 語法範例 6  
  
```  
val 'testmulti' = m 'String 1\0String 2\0'  
```  
  
 指定索引鍵名稱 `testmulti` 是 multistring 的值所組成的 `String 1` 和 `String 2`。  
  
### 語法範例 7  
  
```  
val 'testhex' = d '&H55'  
```  
  
 指定索引鍵名稱 `testhex` 是 **DWORD** 值設定為十六進位 55 \(十進位 85\)。  請注意這個格式遵守 **\_&H** 附註 Visual Basic 規格中找到。  
  
## 請參閱  
 [Creating Registrar Scripts](../atl/creating-registrar-scripts.md)