---
title: ATL 註冊機構和剖析樹狀結構
ms.date: 11/04/2016
helpviewer_keywords:
- parse trees
ms.assetid: 668ce2dd-a1c3-4ca0-8135-b25267cb6a85
ms.openlocfilehash: de2cea9b0e7b7c62236f708f9aa8217eaa5df51d
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168692"
---
# <a name="understanding-parse-trees"></a>瞭解剖析樹狀結構

您可以在註冊機構腳本中定義一或多個剖析樹，其中每個剖析樹狀結構的格式如下：

> \<根機碼>\<{登錄運算式>} +

其中：

> \<根機碼>：： = HKEY_CLASSES_ROOT |HKEY_CURRENT_USER | \
> &nbsp;&nbsp;&nbsp;&nbsp;HKEY_LOCAL_MACHINE |HKEY_USERS | \
> &nbsp;&nbsp;&nbsp;&nbsp;HKEY_PERFORMANCE_DATA |HKEY_DYN_DATA | \
> &nbsp;&nbsp;&nbsp;&nbsp;HKEY_CURRENT_CONFIG |HKCR |HKCU | \
> &nbsp;&nbsp;&nbsp;&nbsp;HKLM |HKU |HKPD |HKDD |HKCC

> \<登錄運算式>：： = \<新增金鑰> |\<刪除金鑰>

> \<Add key>：： = [**ForceRemove** | **NoRemove** | **val**]\<機碼名稱>\<[索引鍵值>] [\<{Add Key>}]

> \<刪除金鑰>：： =**刪除**\<索引鍵名稱>

> \<索引鍵名稱>：： = **'**\<英數位元>+**'**

> \<英數位元>：： =*任何字元 NOT Null，亦即 ASCII 0*

> \<金鑰值>：： = \<金鑰類型>\<索引鍵名稱>

> \<金鑰類型>：： = **s** | **d**

> \<金鑰值>：： = **'**\<英數位元>**'**

> [!NOTE]
> `HKEY_CLASSES_ROOT`和`HKCR`相等;`HKEY_CURRENT_USER`和`HKCU`相等;以此類推。

剖析樹狀結構可以將多個索引鍵和子\<機碼新增至> 的根金鑰。 在此情況下，它會將子機碼的控制碼保持開啟，直到剖析器完成其所有子機碼的剖析為止。 這個方法比一次操作單一索引鍵更有效率，如下列範例所示：

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

在這裡，註冊機構一開始會開啟`HKEY_CLASSES_ROOT\MyVeryOwnKey`（建立）。 接著會看到具有`MyVeryOwnKey`子機碼的。 註冊機構會保留控制碼`MyVeryOwnKey`，並使用此父控制碼開啟（建立） `HasASubKey` ，而不是關閉的金鑰。 （當沒有任何父控制碼開啟時，系統登錄可能會變慢）。因此，以`HKEY_CLASSES_ROOT\MyVeryOwnKey`作為父系開啟`HasASubKey`和`MyVeryOwnKey`開啟的速度會比開啟`MyVeryOwnKey`、關閉`MyVeryOwnKey`和開啟`MyVeryOwnKey\HasASubKey`更快。

## <a name="see-also"></a>另請參閱

[建立註冊機構腳本](../atl/creating-registrar-scripts.md)
