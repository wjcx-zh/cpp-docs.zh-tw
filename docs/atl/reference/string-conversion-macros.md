---
title: 字串轉換巨集
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
ms.openlocfilehash: 8df496b78334d26e7d3664642b2e9d93d6149843
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325845"
---
# <a name="string-conversion-macros"></a>字串轉換巨集

這些宏提供字串轉換功能。

## <a name="atl-and-mfc-string-conversion-macros"></a><a name="atl_and_mfc_string_conversion_macros"></a>ATL 與 MFC 字串轉換巨集

這裡討論的字串轉換巨集對於 ATL 及 MFC 而言都有效。 有關 MFC 字串轉換的詳細資訊,請參閱[TN059:使用 MFC MBCS/Unicode 轉換巨集](../../mfc/tn059-using-mfc-mbcs-unicode-conversion-macros.md)和[MFC 宏和全域](../../mfc/reference/mfc-macros-and-globals.md)。

## <a name="devmode-and-textmetric-string-conversion-macros"></a><a name="devmode_and_textmetric_string_conversion_macros"></a>DEVMODE 與 TEXTMETRIC 字串轉換巨集

這些巨集創建[DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea)或[TEXTMETRIC](/windows/win32/api/wingdi/ns-wingdi-textmetricw)結構的副本,並將新結構中的字串轉換為新的字串類型。 宏為新結構在堆疊上分配內存,並返回指向新結構的指標。

```cpp
MACRONAME( address_of_structure )
```

### <a name="remarks"></a>備註

例如：

[!code-cpp[NVC_ATL_Utilities#128](../../atl/codesnippet/cpp/string-conversion-macros_1.cpp)]

以及：

[!code-cpp[NVC_ATL_Utilities#129](../../atl/codesnippet/cpp/string-conversion-macros_2.cpp)]

在巨集名稱中,源結構中的字串類型位於左側(例如**A),** 目標結構中的字串類型位於右側(例如 **,W**)。 **代表**LPSTR,OLE**OLE**代表 LPOLESTR,T 代表 LPTSTR,W**T****W**代表 LPWSTR。

因此,DEVMODEA2W`DEVMODE`將 帶有 LPSTR 字`DEVMODE`串的結構 複製到具有 LPWSTR 字串的結構中,TEXTMETRICOLE2T 將帶有`TEXTMETRIC`LPOLESTR 字串的結構複製到具有`TEXTMETRIC`LPTSTR 字串的結構中,等等。

結構中轉換的`DEVMODE`兩個字串是裝置名稱`dmDeviceName`( ) 與`dmFormName`表單名稱 ( ) ( ) 字串`DEVMODE`轉換宏還更新結構大小 ()。`dmSize`

結構中轉換`TEXTMETRIC`的四個字串是第一個字元 ()、`tmFirstChar`最後一個字`tmLastChar`元 ()、默認`tmDefaultChar`字元 () 和`tmBreakChar`中斷字元 ()。

`DEVMODE`和`TEXTMETRIC`字串轉換宏的行為取決於有效的編譯器指令(如果有)。 如果來源與目的類型相同，則不會發生轉換。 編譯器指令更改**T**和**OLE**如下所示:

|作用中的編譯器指示詞|T 變為|OLE 變為|
|----------------------------------|---------------|-----------------|
|無|**A**|**W**|
|**\_Unicode**|**W**|**W**|
|**奧萊2ANSI**|**A**|**A**|
|UNICODE 與**OLE2ANSI** ** \_ **|**W**|**A**|

下表列出了`DEVMODE``TEXTMETRIC`和字串轉換宏。

|||
|-|-|
|德沃莫達2W|TEXTMETRICA2W|
|德莫多爾2T|TEXTMETRICOLE2T|
|德莫德特2OLE|TEXTMETRICT2OLE|
|德沃格W2A|TEXTMETRICW2A|

## <a name="see-also"></a>另請參閱

[巨集](../../atl/reference/atl-macros.md)
