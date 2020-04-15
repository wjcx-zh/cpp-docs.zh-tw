---
title: 註冊表文稿範例
ms.date: 11/04/2016
helpviewer_keywords:
- scripting, examples
- registrar scripts [ATL]
- scripts, Registrar scripts
- registry, Registrar
ms.assetid: b6df80e1-e08b-40ee-9243-9b381b172460
ms.openlocfilehash: 7bcdb7076982e2f0bd08f4fd82bb45f21e61ef20
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329332"
---
# <a name="registry-scripting-examples"></a>註冊表文稿範例

本主題中的文本範例展示如何向系統註冊表添加密鑰、註冊註冊商 COM 伺服器以及指定多個解析樹。

## <a name="add-a-key-to-hkey_current_user"></a>新增金鑰以HKEY_CURRENT_USER

以下分析樹說明瞭向系統註冊表添加單個密鑰的簡單腳本。 特別是,文稿將鍵`MyVeryOwnKey`新增`HKEY_CURRENT_USER`到 。 它還將`HowGoesIt`的 預設字串值分配給新鍵:

```
HKEY_CURRENT_USER
{
    'MyVeryOwnKey' = s 'HowGoesIt'
}
```

此腳本可以輕鬆擴展以定義多個子鍵,如下所示:

```
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

現在,文稿將子鍵`HasASubkey`加入`MyVeryOwnKey`。 到此子鍵,它同時`PrettyCool`添加子鍵(預設值`DWORD`為 55)`ANameValue`和 命名值(字串值`WithANamedValue`為 )。

## <a name="register-the-registrar-com-server"></a><a name="_atl_register_the_registrar_com_server"></a>註冊註冊商 COM 伺服器

以下文本註冊註冊商 COM 伺服器本身。

```
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

在執行時,此解析樹將`ATL.Registrar`鍵加入`HKEY_CLASSES_ROOT`。 到此新金鑰,它然後:

- 指定`ATL Registrar Class`為鍵的預設字串值。

- 添加`CLSID`為子鍵。

- 指定`{44EC053A-400F-11D0-9DCD-00A0C90391D3}``CLSID`指定 。 (此值是註冊器的 CLSID,`CoCreateInstance`用於 .

由於`CLSID`是共用的,因此不應在取消註冊模式下將其刪除。 `NoRemove CLSID`語句 ,`CLSID`通過指示 應在註冊模式下打開並在取消註冊模式下忽略來這樣做。

語句`ForceRemove`通過在重新創建密鑰之前刪除鍵及其所有子鍵來提供內務管理功能。 如果子鍵的名稱已更改,這非常有用。 在此文稿示例中,`ForceRemove`檢查是否存在`{44EC053A-400F-11D0-9DCD-00A0C90391D3}`。 如果是, `ForceRemove`

- 遞歸刪除`{44EC053A-400F-11D0-9DCD-00A0C90391D3}`及其所有子鍵。

- 重新建立`{44EC053A-400F-11D0-9DCD-00A0C90391D3}`。

- 新增`ATL Registrar Class`預設字串值`{44EC053A-400F-11D0-9DCD-00A0C90391D3}`。

解析樹現在向`{44EC053A-400F-11D0-9DCD-00A0C90391D3}`中添加了兩個新的子鍵。 第一個鍵`ProgID`獲取預設字串值,該值是 ProgID。 第二個鍵`InprocServer32`獲取預設字串值`%MODULE%`,這是本文"[使用可替換參數(註冊器的預處理器")](../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md)部分中解釋的預處理器值。 `InprocServer32`還取得命名值`ThreadingModel`, 字串值`Apartment`為 。

## <a name="specify-multiple-parse-trees"></a>指定多個分析樹

要在腳本中指定多個解析樹,只需將一個樹放在另一個樹的末尾即可。 例如,以下文稿會鍵`MyVeryOwnKey`, 加入與`HKEY_CLASSES_ROOT``HKEY_CURRENT_USER`的解析樹中:

```
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
> 在註冊器腳本中,4K 是最大令牌大小。 (令牌是語法中的任何可識別元素。在前面的腳本`HKCR`示例中`HKEY_CURRENT_USER`,`'MyVeryOwnKey'``'HowGoesIt'`和 都是權杖。

## <a name="see-also"></a>另請參閱

[建立註冊器文稿](../atl/creating-registrar-scripts.md)
