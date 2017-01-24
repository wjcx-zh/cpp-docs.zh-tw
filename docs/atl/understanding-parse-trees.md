---
title: "Understanding Parse Trees | Microsoft Docs"
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
  - "parse trees"
ms.assetid: 668ce2dd-a1c3-4ca0-8135-b25267cb6a85
caps.latest.revision: 12
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Understanding Parse Trees
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您可以定義一或多個以登錄器指令碼的剖析樹狀結構中，每個剖析樹狀結構的形式如下:  
  
```  
<root key>{<registry expression>}+  
```  
  
 其中：  
  
```  
<root key> ::=  HKEY_CLASSES_ROOT | HKEY_CURRENT_USER |  
               HKEY_LOCAL_MACHINE | HKEY_USERS |  
               HKEY_PERFORMANCE_DATA | HKEY_DYN_DATA |  
               HKEY_CURRENT_CONFIG | HKCR | HKCU |  
               HKLM | HKU | HKPD | HKDD | HKCC  
<registry expression> ::= <Add Key> | <Delete Key>  
<Add Key> ::= [ForceRemove | NoRemove | val]<Key Name>  
              [<Key Value>][{< Add Key>}]  
<Delete Key> ::=  Delete<Key Name>  
<Key Name> ::= '<AlphaNumeric>+'  
<AlphaNumeric> ::= any character not NULL, i.e. ASCII 0  
<Key Value> ::== <Key Type><Key Name>  
<Key Type> ::= s | d  
<Key Value> ::= '<AlphaNumeric>'  
```  
  
> [!NOTE]
>  `HKEY_CLASSES_ROOT` 和 `HKCR` 相等; `HKEY_CURRENT_USER` 和 `HKCU` 相等;等等。  
  
 剖析樹狀結構可加入多個索引鍵和子機碼加入 \<root key\>。  在這個案例中，它會保持子機碼的控制代碼開啟，直到剖析器剖析其所有子機碼。  這個方法會一次運作更有效地在單一索引鍵，如以下範例所示:  
  
```  
HKEY_CLASSES_ROOT  
{  
   'MyVeryOwnKey'  
   {  
      'HasASubKey'  
      {  
         'PrettyCool?'  
      }  
   }  
}  
```  
  
 在這裡，管理員一開始開啟 \(透過建立\) `HKEY_CLASSES_ROOT\MyVeryOwnKey`。  然後參閱 `MyVeryOwnKey` 有一個子機碼。  不要關閉機碼為 `MyVeryOwnKey`，管理員將控制代碼並開啟 \(\) 會使用這個父控制代碼， `HasASubKey` 。  \(系統登錄可能較慢，當父控制代碼尚未開啟\)。因此，開啟 `HKEY_CLASSES_ROOT\MyVeryOwnKey` 然後開啟 `HasASubKey` 和 `MyVeryOwnKey` 做為父來開啟 `MyVeryOwnKey`，結尾 `MyVeryOwnKey`，然後開啟快速 `MyVeryOwnKey\HasASubKey`。  
  
## 請參閱  
 [Creating Registrar Scripts](../atl/creating-registrar-scripts.md)