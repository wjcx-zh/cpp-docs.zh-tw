---
title: "ATL 登錄器和 Backus-naur Nauer 形成 (BNF) 語法 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- BNF notation
- Backus Nauer Form (BNF) syntax
ms.assetid: 994bbef0-9077-4aa8-bdfe-b7e830af9acc
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 01d364313420c0a950f8eba222e3ae020fbd86cf
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="understanding-backus-nauer-form-bnf-syntax"></a>了解 Nauer Backus-naur 格式 (BNF) 語法
使用 ATL 登錄器指令碼會使用 BNF 語法，使用下表所示的標記法本主題中所述。  
  
|慣例/符號|意義|  
|------------------------|-------------|  
|`::=`|對等項目|  
|`&#124;`|OR|  
|`X+`|一或多個`X`s。|  
|`[X]`|`X` 是選擇項。 以代表選擇性分隔符號`[]`。|  
|任何**粗體**文字|字串常值。|  
|任何*設為斜體*文字|如何建構字串常值。|  
  
 上表所示，登錄器指令碼會使用字串常值。 這些值是必須出現在您的指令碼中的實際文字。 下表描述 ATL 登錄器指令碼中使用的字串常值。  
  
|字串常值|動作|  
|--------------------|------------|  
|**ForceRemove**|完全移除的下一個鍵 （如果有的話），然後重新建立。|  
|**NoRemove**|取消註冊期間不會移除下一個索引鍵。|  
|**val**|指定`<Key Name>`實際上是具名的值。|  
|**刪除**|在登錄期間刪除下一個索引鍵。|  
|**s**|指定的下一個值是字串 (**REG_SZ**)。|  
|**d**|指定下一個值為**DWORD** (**REG_DWORD**)。|  
|**m**|指定的下一個值是在 multistring (**REG_MULTI_SZ**)。|  
|**b**|指定的下一個值是二進位值 (**REG_BINARY**)。|  
  
## <a name="bnf-syntax-examples"></a>BNF 語法範例  
 以下是一些可協助您了解的標記法和字串常值中的 ATL 登錄器指令碼的運作方式的語法範例。  
  
### <a name="syntax-example-1"></a>語法範例 1  
  
```  
<registry expression> ::= <Add Key>  
```  
  
 指定`registry expression`相當於`Add Key`。  
  
### <a name="syntax-example-2"></a>語法範例 2  
  
```  
<registry expression> ::= <Add Key> | <Delete Key>  
```  
  
 指定`registry expression`相當於`Add Key`或`Delete Key`。  
  
### <a name="syntax-example-3"></a>語法範例 3  
  
```  
<Key Name> ::= '<AlphaNumeric>+'  
```  
  
 指定`Key Name`相當於一個或多個`AlphaNumerics`。  
  
### <a name="syntax-example-4"></a>語法範例 4  
  
```  
<Add Key> ::= [ForceRemove | NoRemove | val]<Key Name>  
```  
  
 指定`Add Key`相當於`Key Name`，且字串常值`ForceRemove`， `NoRemove`，和`val`，是選擇性的。  
  
### <a name="syntax-example-5"></a>語法範例 5  
  
```  
<AlphaNumeric> ::= any character not NULL, that is, ASCII 0  
```  
  
 指定`AlphaNumeric`相當至任何非 NULL 字元。  
  
### <a name="syntax-example-6"></a>語法範例 6  
  
```  
val 'testmulti' = m 'String 1\0String 2\0'  
```  
  
 指定的索引鍵名稱`testmulti`multistring 值組成`String 1`和`String 2`。  
  
### <a name="syntax-example-7"></a>語法範例 7  
  
```  
val 'testhex' = d '&H55'  
```  
  
 指定的索引鍵名稱`testhex`是**DWORD**值設定為十六進位 55 (十進位 85)。 請注意，此格式符合**& H** Visual Basic 規格中找到的標記法為。  
  
## <a name="see-also"></a>請參閱  
 [建立登錄器指令碼](../atl/creating-registrar-scripts.md)

