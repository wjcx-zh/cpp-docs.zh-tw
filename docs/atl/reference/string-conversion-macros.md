---
title: 字串轉換宏
ms.date: 11/04/2016
f1_keywords:
- atlconv/ATL::DEVMODEA2W
- atlconv/ATL::TEXTMETRICA2W
- atlconv/ATL::DEVMODEOLE2T
- atlconv/ATL::TEXTMETRICOLE2T
- atlconv/ATL::DEVMODET2OLE
- atlconv/ATL::TEXTMETRICT2OLE
- atlconv/ATL::DEVMODEW2A
- atlconv/ATL::TEXTMETRICW2A
ms.assetid: 2ff7c0b6-2bde-45fe-897f-6128e18e0c27
ms.openlocfilehash: 6a84424de81eba2e6ab1e1baf60f567ebf2739ee
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2019
ms.locfileid: "68915511"
---
# <a name="string-conversion-macros"></a>字串轉換宏

這些宏會提供字串轉換功能。

##  <a name="atl_and_mfc_string_conversion_macros"></a>ATL 和 MFC 字串轉換宏

這裡討論的字串轉換巨集對於 ATL 及 MFC 而言都有效。 如需 MFC 字串轉換的詳細資訊, [請參閱 TN059:使用 mfc MBCS/Unicode 轉換宏](../../mfc/tn059-using-mfc-mbcs-unicode-conversion-macros.md)和[mfc 宏和 Globals](../../mfc/reference/mfc-macros-and-globals.md)。

##  <a name="devmode_and_textmetric_string_conversion_macros"></a>DEVMODE 和 TEXTMETRIC 字串轉換宏

這些宏會建立[DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea)或[TEXTMETRIC](/windows/desktop/api/wingdi/ns-wingdi-tagtextmetrica)結構的複本, 並將新結構內的字串轉換成新的字串類型。 宏會針對新的結構在堆疊上配置記憶體, 並傳回新結構的指標。

```cpp
MACRONAME( address_of_structure )
```

### <a name="remarks"></a>備註

例如：

[!code-cpp[NVC_ATL_Utilities#128](../../atl/codesnippet/cpp/string-conversion-macros_1.cpp)]

以及：

[!code-cpp[NVC_ATL_Utilities#129](../../atl/codesnippet/cpp/string-conversion-macros_2.cpp)]

在宏名稱中, 來源結構中的字串類型是在左邊 (例如), 而目的地結構中的字串類型則是在右邊 (例如**W**)。 **A**代表 LPSTR, **OLE**代表 LPOLESTR, **T**代表 LPTSTR, **W**代表 LPWSTR。

因此, DEVMODEA2W 會將`DEVMODE`含有 LPSTR 字串的結構複製`DEVMODE`到具有 LPWSTR `TEXTMETRIC`字串的結構中, TEXTMETRICOLE2T 會將具有 LPOLESTR 字串`TEXTMETRIC`的結構複製到具有 LPTSTR 字串的結構中等等。

`DEVMODE`結構中轉換的兩個字串是裝置名稱 (`dmDeviceName`) 和表單名稱 (`dmFormName`)。 字串轉換宏也會更新結構大小 (`dmSize`)。 `DEVMODE`

`TEXTMETRIC`結構中轉換的四個字串是第一個字元 (`tmFirstChar`)、最後一個字元 (`tmLastChar`)、預設字元 (`tmDefaultChar`) 和 break 字元 (`tmBreakChar`)。

`DEVMODE` 和`TEXTMETRIC`字串轉換宏的行為取決於作用中的編譯器指示詞 (如果有的話)。 如果來源與目的類型相同，則不會發生轉換。 編譯器指示詞會變更**T**和**OLE** , 如下所示:

|作用中的編譯器指示詞|T 變為|OLE 變為|
|----------------------------------|---------------|-----------------|
|none|**A**|**W**|
|**\_消除**|**W**|**W**|
|**OLE2ANSI**|**A**|**A**|
|UNICODE 和**OLE2ANSI** **\_**|**W**|**A**|

下表列出`DEVMODE`和`TEXTMETRIC`字串轉換宏。

|||
|-|-|
|DEVMODEA2W|TEXTMETRICA2W|
|DEVMODEOLE2T|TEXTMETRICOLE2T|
|DEVMODET2OLE|TEXTMETRICT2OLE|
|DEVMODEW2A|TEXTMETRICW2A|

## <a name="see-also"></a>另請參閱

[巨集](../../atl/reference/atl-macros.md)
