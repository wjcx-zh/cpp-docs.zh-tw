---
title: ATL 登錄器和剖析樹狀結構
ms.date: 11/04/2016
helpviewer_keywords:
- parse trees
ms.assetid: 668ce2dd-a1c3-4ca0-8135-b25267cb6a85
ms.openlocfilehash: e1aea573e78e6f6a9a86bc4e3987ee448815f329
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62196164"
---
# <a name="understanding-parse-trees"></a>了解剖析樹狀結構

您可以定義一或多個剖析樹狀目錄中您的註冊機構指令碼，其中每個剖析樹狀結構具有下列格式：

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
<Add Key> ::= [ForceRemove | NoRemove | val]<Key Name> [<Key Value>][{<Add Key>}]
<Delete Key> ::= Delete<Key Name>
<Key Name> ::= '<AlphaNumeric>+'
<AlphaNumeric> ::= any character not NULL, i.e. ASCII 0
<Key Value> ::== <Key Type><Key Name>
<Key Type> ::= s | d
<Key Value> ::= '<AlphaNumeric>'
```

> [!NOTE]
> `HKEY_CLASSES_ROOT` 和`HKCR`相等`HKEY_CURRENT_USER`和`HKCU`是對等，依此類推。

剖析樹狀結構可以新增多個索引鍵和子機碼\<根目錄機碼 >。 在此情況下，它將保持子機碼的控制代碼為開啟狀態，直到剖析器完成剖析所有子機碼。 這種方法是更有效率，比起單一索引鍵，一次，如下列範例所示：

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

在這裡，註冊機構一開始會開啟 （建立） `HKEY_CLASSES_ROOT\MyVeryOwnKey`。 然後會看到，`MyVeryOwnKey`有子機碼。 而不是關閉的索引鍵`MyVeryOwnKey`，註冊機構保留的控制代碼，並開啟 （建立）`HasASubKey`使用此父控制代碼。 （沒有父控制代碼開啟時系統登錄會比較慢）。因此，開啟`HKEY_CLASSES_ROOT\MyVeryOwnKey`，然後開啟`HasASubKey`具有`MyVeryOwnKey`為父代的速度比開啟`MyVeryOwnKey`，正在關閉`MyVeryOwnKey`，然後開啟`MyVeryOwnKey\HasASubKey`。

## <a name="see-also"></a>另請參閱

[建立登錄器指令碼](../atl/creating-registrar-scripts.md)
