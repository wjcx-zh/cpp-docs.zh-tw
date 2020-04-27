---
title: 登入指令檔範例
ms.date: 11/04/2016
helpviewer_keywords:
- scripting, examples
- registrar scripts [ATL]
- scripts, Registrar scripts
- registry, Registrar
ms.assetid: b6df80e1-e08b-40ee-9243-9b381b172460
ms.openlocfilehash: 0e225ce28309aa619fd9436d8f4b93e60544e86c
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168744"
---
# <a name="registry-scripting-examples"></a>登入指令檔範例

本主題中的腳本範例示範如何將金鑰新增至系統登錄、註冊註冊機構 COM 伺服器，以及指定多個剖析樹狀目錄。

## <a name="add-a-key-to-hkey_current_user"></a>將金鑰新增至 HKEY_CURRENT_USER

下列剖析樹狀結構說明將單一按鍵新增至系統登錄的簡單腳本。 特別是，腳本會將索引鍵`MyVeryOwnKey`新增至。 `HKEY_CURRENT_USER` 它也會將的預設字串值`HowGoesIt`指派給新的索引鍵：

```rgs
HKEY_CURRENT_USER
{
    'MyVeryOwnKey' = s 'HowGoesIt'
}
```

您可以輕鬆地擴充此腳本，以定義多個子機碼，如下所示：

```rgs
HKCU
{
    'MyVeryOwnKey' = s 'HowGoesIt'
    {
        'HasASubkey'
        {
            'PrettyCool' = d '55'
            val 'ANameValue' = s 'WithANamedValue'
        }
    }
}
```

現在，腳本會將子`HasASubkey`機碼加入至`MyVeryOwnKey`。 在這個子機碼中，它`PrettyCool`會同時新增子機`DWORD`碼（預設值為 55 `ANameValue` ）和指定的值（具有的`WithANamedValue`字串值）。

## <a name="register-the-registrar-com-server"></a><a name="_atl_register_the_registrar_com_server"></a>註冊註冊機構 COM 伺服器

下列腳本會註冊註冊機構 COM 伺服器本身。

```rgs
HKCR
{
    ATL.Registrar = s 'ATL Registrar Class'
    {
        CLSID = s '{44EC053A-400F-11D0-9DCD-00A0C90391D3}'
    }
    NoRemove CLSID
    {
        ForceRemove {44EC053A-400F-11D0-9DCD-00A0C90391D3} = s 'ATL Registrar Class'
        {
            ProgID = s 'ATL.Registrar'
            InprocServer32 = s '%MODULE%'
            {
                val ThreadingModel = s 'Apartment'
            }
        }
    }
}
```

在執行時間，這個剖析樹狀目錄會`ATL.Registrar`將索引`HKEY_CLASSES_ROOT`鍵新增至。 在這個新的機碼中，它會：

- 指定`ATL Registrar Class`做為索引鍵的預設字串值。

- 加入`CLSID`做為子機碼。

- 指定`{44EC053A-400F-11D0-9DCD-00A0C90391D3}`的`CLSID`。 （此值是與`CoCreateInstance`搭配使用的註冊機構的 CLSID）。

由於`CLSID`是共用的，因此不應該在取消註冊模式中移除。 語句`NoRemove CLSID`會藉由指出`CLSID`應該在註冊模式中開啟，並在取消註冊模式中忽略，來執行這項工作。

`ForceRemove`語句會在重新建立金鑰之前，先移除索引鍵及其所有子機碼，以提供內務處理功能。 如果子機碼的名稱已變更，這會很有用。 在此腳本範例中`ForceRemove` ，會檢查是否`{44EC053A-400F-11D0-9DCD-00A0C90391D3}`已存在。 如果有， `ForceRemove`：

- 遞迴刪除`{44EC053A-400F-11D0-9DCD-00A0C90391D3}`及其所有子機碼。

- 重新建立`{44EC053A-400F-11D0-9DCD-00A0C90391D3}`。

- 加入`ATL Registrar Class`做為的預設字串值`{44EC053A-400F-11D0-9DCD-00A0C90391D3}`。

剖析樹狀結構現在會在`{44EC053A-400F-11D0-9DCD-00A0C90391D3}`中加入兩個新的子機碼。 第一個索引鍵`ProgID`會取得做為 ProgID 的預設字串值。 第二個索引`InprocServer32`鍵會取得預設字串值， `%MODULE%`這是本文中[使用可取代參數（註冊機構的預處理器）](../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md)一節所說明的預處理器值。 `InprocServer32`也會取得名為的`ThreadingModel` `Apartment`值，其字串值為。

## <a name="specify-multiple-parse-trees"></a>指定多個剖析樹狀結構

若要在腳本中指定一個以上的剖析樹狀結構，只要將一個樹狀結構放在另一個樹狀目錄的結尾。 例如，下列腳本會將索引鍵`MyVeryOwnKey`新增至`HKEY_CLASSES_ROOT`和`HKEY_CURRENT_USER`的剖析樹：

```rgs
HKCR
{
    'MyVeryOwnKey' = s 'HowGoesIt'
}
HKEY_CURRENT_USER
{
    'MyVeryOwnKey' = s 'HowGoesIt'
}
```

> [!NOTE]
> 在註冊機構腳本中，4K 是 token 大小的上限。 （Token 是語法中任何可辨識的元素）。在先前的腳本範例中`HKCR`， `HKEY_CURRENT_USER`、 `'MyVeryOwnKey'`、和`'HowGoesIt'`都是所有權杖。

## <a name="see-also"></a>另請參閱

[建立註冊機構腳本](../atl/creating-registrar-scripts.md)
