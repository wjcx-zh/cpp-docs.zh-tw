---
title: ATL 註冊機構和剖析樹
ms.date: 11/04/2016
helpviewer_keywords:
- parse trees
ms.assetid: 668ce2dd-a1c3-4ca0-8135-b25267cb6a85
ms.openlocfilehash: ff74ff879e757a569232ff19244d3f7598063465
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2020
ms.locfileid: "90040284"
---
# <a name="understanding-parse-trees"></a>瞭解剖析樹狀結構

您可以在註冊機構腳本中定義一個或多個剖析樹狀結構，其中每個剖析樹狀結構的格式如下：

> \<root key>{\<registry expression>}+

其中：

> \<root key> ：： = HKEY_CLASSES_ROOT \| HKEY_CURRENT_USER \|\
> &emsp;HKEY_LOCAL_MACHINE \| HKEY_USERS \|\
> &emsp;HKEY_PERFORMANCE_DATA \| HKEY_DYN_DATA \|\
> &emsp;HKEY_CURRENT_CONFIG \| HKCR \| HKCU \|\
> &emsp;HKLM \| HKU \| HKPD \| HKDD \| HKCC

> \<registry expression>::= \<Add Key> \|\<Delete Key>

> \<Add Key>：： = \[ **ForceRemove** \| **NoRemove** \| **val**] \<Key Name> [ \<Key Value> ] [{ \<Add Key> }]

> \<Delete Key> ：： = **刪除**\<Key Name>

> \<Key Name> ::= **'**\<AlphaNumeric>+**'**

> \<AlphaNumeric> ：： = *任何不是 Null 的字元，亦即 ASCII 0*

> \<Key Value> ::= \<Key Type>\<Key Name>

> \<Key Type> ：： = **s** \| **d**

> \<Key Value> ::= **'**\<AlphaNumeric>**'**

> [!NOTE]
> `HKEY_CLASSES_ROOT` 和相等，而且相等， `HKCR` `HKEY_CURRENT_USER` `HKCU` 以此類推。

剖析樹狀結構可以將多個索引鍵和子機碼加入至 \<root key> 。 如此一來，它會讓子機碼的控制碼保持開啟，直到剖析器完成其所有子機碼剖析為止。 這種方法比單一索引鍵一次運作更有效率，如下列範例所示：

```rgs
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

在這裡，註冊機構一開始會開啟 (建立) `HKEY_CLASSES_ROOT\MyVeryOwnKey` 。 然後，它會看到 `MyVeryOwnKey` 有子機碼。 `MyVeryOwnKey`註冊機構會保留控制碼，而不是關閉金鑰，而是 `HasASubKey` 使用此父控制碼 (建立) 。  (當沒有任何父控制碼開啟時，系統登錄可能會變慢 ) 。如此一來， `HKEY_CLASSES_ROOT\MyVeryOwnKey` `HasASubKey` `MyVeryOwnKey` 以父系的形式開啟然後開啟，會比開啟、關閉和開啟的速度還要快 `MyVeryOwnKey` `MyVeryOwnKey` `MyVeryOwnKey\HasASubKey` 。

## <a name="see-also"></a>另請參閱

[建立註冊機構腳本](../atl/creating-registrar-scripts.md)
