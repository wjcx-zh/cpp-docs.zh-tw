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
ms.openlocfilehash: 60cccebf4e1db8369ea5a88f04a37b96838ff49f
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88835151"
---
# <a name="string-conversion-macros"></a>字串轉換宏

這些宏提供字串轉換功能。

## <a name="atl-and-mfc-string-conversion-macros"></a><a name="atl_and_mfc_string_conversion_macros"></a> ATL 和 MFC 字串轉換宏

這裡討論的字串轉換巨集對於 ATL 及 MFC 而言都有效。 如需 MFC 字串轉換的詳細資訊，請參閱 [TN059：使用 MFC MBCS/Unicode 轉換宏](../../mfc/tn059-using-mfc-mbcs-unicode-conversion-macros.md) 和 [Mfc 宏和全域](../../mfc/reference/mfc-macros-and-globals.md)。

## <a name="devmode-and-textmetric-string-conversion-macros"></a><a name="devmode_and_textmetric_string_conversion_macros"></a> DEVMODE 和 TEXTMETRIC 字串轉換宏

這些宏會建立 [DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea) 或 [TEXTMETRIC](/windows/win32/api/wingdi/ns-wingdi-textmetricw) 結構的複本，並將新結構內的字串轉換成新的字串類型。 宏會在堆疊上配置新結構的記憶體，並將指標傳回至新的結構。

```cpp
MACRONAME( address_of_structure )
```

### <a name="remarks"></a>備註

例如：

[!code-cpp[NVC_ATL_Utilities#128](../../atl/codesnippet/cpp/string-conversion-macros_1.cpp)]

以及：

[!code-cpp[NVC_ATL_Utilities#129](../../atl/codesnippet/cpp/string-conversion-macros_2.cpp)]

在宏名稱中，來源結構中的字串類型是在左邊 (例如 **，) ，** 目的結構中的字串類型是在右邊 (例如 **W**) 。 **A** 代表 LPSTR、 **OLE** 代表 LPOLESTR、 **T** 代表 LPTSTR， **W** 代表 LPWSTR。

因此，DEVMODEA2W 會將 `DEVMODE` 包含 LPSTR 字串的結構複製到 `DEVMODE` 具有 LPWSTR 字串的結構中，TEXTMETRICOLE2T 會將 `TEXTMETRIC` 具有 LPOLESTR 字串的結構複製到 `TEXTMETRIC` 具有 LPTSTR 字串的結構中，依此類推。

結構中轉換的兩個字串 `DEVMODE` 是 () 的裝置名稱 `dmDeviceName` ，以及 () 的表單名稱 `dmFormName` 。 `DEVMODE`字串轉換宏也會更新結構大小 (`dmSize`) 。

結構中轉換的四個字串為 `TEXTMETRIC` 第一個字元 (`tmFirstChar`) 、最後一個字元 (`tmLastChar`) 、預設字元 (`tmDefaultChar`) 和 break 字元 (`tmBreakChar`) 。

`DEVMODE`和 `TEXTMETRIC` 字串轉換宏的行為取決於作用中的編譯器指示詞（如果有的話）。 如果來源與目的類型相同，則不會發生轉換。 編譯器指示詞會變更 **T** 和 **OLE** ，如下所示：

|作用中的編譯器指示詞|T 變為|OLE 變為|
|----------------------------------|---------------|-----------------|
|無|**A**|**W**|
|**\_UNICODE**|**W**|**W**|
|**OLE2ANSI**|**A**|**A**|
|** \_ UNICODE**和**OLE2ANSI**|**W**|**A**|

下表列出 `DEVMODE` 和 `TEXTMETRIC` 字串轉換宏。

|`DEVMODE` 宏觀|`TEXTMETRIC` 宏觀|
|-|-|
|DEVMODEA2W|TEXTMETRICA2W|
|DEVMODEOLE2T|TEXTMETRICOLE2T|
|DEVMODET2OLE|TEXTMETRICT2OLE|
|DEVMODEW2A|TEXTMETRICW2A|

## <a name="see-also"></a>另請參閱

[巨集](../../atl/reference/atl-macros.md)
