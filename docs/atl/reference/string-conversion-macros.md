---
title: 字串轉換巨集 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlconv/ATL::DEVMODEA2W
- atlconv/ATL::TEXTMETRICA2W
- atlconv/ATL::DEVMODEOLE2T
- atlconv/ATL::TEXTMETRICOLE2T
- atlconv/ATL::DEVMODET2OLE
- atlconv/ATL::TEXTMETRICT2OLE
- atlconv/ATL::DEVMODEW2A
- atlconv/ATL::TEXTMETRICW2A
dev_langs:
- C++
ms.assetid: 2ff7c0b6-2bde-45fe-897f-6128e18e0c27
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: aa44449c65dbdfdea93004fa2fe1adffdeba033d
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50061733"
---
# <a name="string-conversion-macros"></a>字串轉換巨集

這些巨集提供轉換功能的字串。

##  <a name="atl_and_mfc_string_conversion_macros"></a>  ATL 和 MFC 字串轉換巨集

這裡討論的字串轉換巨集對於 ATL 及 MFC 而言都有效。 如需有關 MFC 字串轉換的詳細資訊，請參閱[TN059： 使用的 MFC MBCS/Unicode 轉換巨集](../../mfc/tn059-using-mfc-mbcs-unicode-conversion-macros.md)並[MFC 巨集和全域](../../mfc/reference/mfc-macros-and-globals.md)。

##  <a name="devmode_and_textmetric_string_conversion_macros"></a>  DEVMODE 和 TEXTMETRIC 字串轉換巨集

這些巨集建立一份[DEVMODE](/windows/desktop/api/wingdi/ns-wingdi-_devicemodea)或是[TEXTMETRIC](/windows/desktop/api/wingdi/ns-wingdi-tagtextmetrica)結構，並將新的結構內的字串轉換成新的字串類型。 巨集為新的結構配置堆疊上的記憶體，並將指標傳回至新的結構。

```cpp
MACRONAME( address_of_structure )
```

### <a name="remarks"></a>備註

例如: 

[!code-cpp[NVC_ATL_Utilities#128](../../atl/codesnippet/cpp/string-conversion-macros_1.cpp)]

以及：

[!code-cpp[NVC_ATL_Utilities#129](../../atl/codesnippet/cpp/string-conversion-macros_2.cpp)]

左邊，在巨集名稱 中，是來源結構中的字串類型 (例如**A**) 和目的地結構中的字串類型會在右側 (比方說， **W**)。 **A** LPSTR，代表**OLE** LPOLESTR，代表**T**代表 LPTSTR，和**W**代表 LPWSTR。

DEVMODEA2W 因此，複製`DEVMODE`LPSTR 結構字串到`DEVMODE`結構的字串 LPWSTR TEXTMETRICOLE2T 複本`TEXTMETRIC`LPOLESTR 結構字串到`TEXTMETRIC`結構和 LPTSTR 字串等等。

轉換中的兩個字串`DEVMODE`結構是裝置名稱 (`dmDeviceName`) 和表單名 (`dmFormName`)。 `DEVMODE`字串轉換巨集也會更新的結構大小 (`dmSize`)。

轉換中的四個字串`TEXTMETRIC`結構是第一個字元 (`tmFirstChar`)，最後一個字元 (`tmLastChar`)，預設的字元 (`tmDefaultChar`)，和符號字元 (`tmBreakChar`)。

行為`DEVMODE`和`TEXTMETRIC`字串轉換巨集取決於編譯器中的指示詞的效果，如果有的話。 如果來源與目的類型相同，則不會發生轉換。 變更編譯器指示詞**T**並**OLE** ，如下所示：

|作用中的編譯器指示詞|T 變為|OLE 變為|
|----------------------------------|---------------|-----------------|
|無|**A**|**W**|
|**\_UNICODE**|**W**|**W**|
|**OLE2ANSI**|**A**|**A**|
|**\_UNICODE**和**OLE2ANSI**|**W**|**A**|

下表列出`DEVMODE`和`TEXTMETRIC`字串轉換巨集。

|||
|-|-|
|DEVMODEA2W|TEXTMETRICA2W|
|DEVMODEOLE2T|TEXTMETRICOLE2T|
|DEVMODET2OLE|TEXTMETRICT2OLE|
|DEVMODEW2A|TEXTMETRICW2A|

## <a name="see-also"></a>另請參閱

[巨集](../../atl/reference/atl-macros.md)
