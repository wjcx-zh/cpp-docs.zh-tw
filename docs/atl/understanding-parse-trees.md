---
title: ATL 登錄器和剖析樹狀結構 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- parse trees
ms.assetid: 668ce2dd-a1c3-4ca0-8135-b25267cb6a85
caps.latest.revision: 12
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c8ce648a541f6e0e2d4fac2e6ee19226e41f20ad
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="understanding-parse-trees"></a>了解剖析樹狀結構
您可以定義一個或多個剖析樹狀結構中登錄器指令碼，其中每個剖析樹狀目錄具有下列格式：  
  
```  
<root key>{<registry expression>}+  
```  
  
 其中：  
  
```  
<root key> ::= HKEY_CLASSES_ROOT | HKEY_CURRENT_USER |  
    HKEY_LOCAL_MACHINE | HKEY_USERS |  
    HKEY_PERFORMANCE_DATA | HKEY_DYN_DATA |  
    HKEY_CURRENT_CONFIG | HKCR | HKCU |  
    HKLM | HKU | HKPD | HKDD | HKCC  
<registry expression> ::= <Add Key> | <Delete Key>  
<Add Key> ::= [ForceRemove | NoRemove | val]<Key Name>  
 [<Key Value>][{<Add Key>}]  
<Delete Key> ::= Delete<Key Name>  
<Key Name> ::= '<AlphaNumeric>+'  
<AlphaNumeric> ::= any character not NULL, i.e. ASCII 0  
<Key Value> ::== <Key Type><Key Name>  
<Key Type> ::= s | d  
<Key Value> ::= '<AlphaNumeric>'  
```  
  
> [!NOTE]
> `HKEY_CLASSES_ROOT`和`HKCR`相等`HKEY_CURRENT_USER`和`HKCU`是對等，依此類推。  
  
 剖析樹狀結構可以加入多個索引鍵和子機碼\<根目錄機碼 >。 在此情況下，它將保持子機碼的控制代碼為開啟狀態，直到完成剖析器剖析所有子機碼。 這種方法是更有效率的單一金鑰操作一次，如下列範例所示：  
  
```  
HKEY_CLASSES_ROOT  
{  
 'MyVeryOwnKey'  
 {  
 'HasASubKey'  
 {  
 'PrettyCool'  
 }  
 }  
}  
```  
  
 在這裡，註冊機構初次開啟 （建立） `HKEY_CLASSES_ROOT\MyVeryOwnKey`。 然後會看到的`MyVeryOwnKey`具有子機碼。 而不是關閉的索引鍵`MyVeryOwnKey`，註冊機構會保留此控制代碼，並開啟 （建立）`HasASubKey`使用此父控制代碼。 （沒有父控制代碼開啟時系統登錄可以是速度較慢）。因此，開啟`HKEY_CLASSES_ROOT\MyVeryOwnKey`，然後開啟`HasASubKey`與`MyVeryOwnKey`為父系的速度比開啟`MyVeryOwnKey`，正在關閉`MyVeryOwnKey`，，然後開啟`MyVeryOwnKey\HasASubKey`。  
  
## <a name="see-also"></a>請參閱  
 [建立登錄器指令碼](../atl/creating-registrar-scripts.md)

