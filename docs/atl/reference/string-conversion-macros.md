---
title: "字串轉換巨集 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
ms.assetid: 2ff7c0b6-2bde-45fe-897f-6128e18e0c27
caps.latest.revision: 16
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: d2d39abf526a58b8442107b5ee816f316ae841f5
ms.openlocfilehash: 634e33f4989046767f17fce15377fe6f4959bd8d
ms.lasthandoff: 03/31/2017

---
# <a name="string-conversion-macros"></a>字串轉換巨集
這些巨集提供轉換功能的字串。  
  
|||  
|-|-|  
|[ATL 和 MFC 字串轉換巨集](string-conversion-macros.md)|字串類型之間轉換的巨集的集合。|  
|[DEVMODE 和 TEXTMETRIC 字串轉換巨集](http://msdn.microsoft.com/library/85cebec0-2a18-48e5-9c1c-99d5b7f15425)|一組內字串轉換的巨集`DEVMODE`和`TEXTMETRIC`結構。|  
  
##  <a name="atl_and_mfc_string_conversion_macros"></a>ATL 和 MFC 字串轉換巨集  
 這裡討論的字串轉換巨集對於 ATL 及 MFC 而言都有效。 如需 MFC 字串轉換的詳細資訊，請參閱[TN059︰ 使用的 MFC MBCS/Unicode 轉換巨集](../../mfc/tn059-using-mfc-mbcs-unicode-conversion-macros.md)和[MFC 巨集和全域](../../mfc/reference/mfc-macros-and-globals.md)。  
  
##  <a name="devmode_and_textmetric_string_conversion_macros"></a>DEVMODE 和 TEXTMETRIC 字串轉換巨集  
 這些巨集建立一份[DEVMODE](http://msdn.microsoft.com/library/windows/desktop/dd183565)或[TEXTMETRIC](http://msdn.microsoft.com/library/windows/desktop/dd145132)結構，並將新的結構中的字串轉換成新的字串類型。 巨集在堆疊上的記憶體配置新的結構，並將指標傳回至新的結構。  
  
```
MACRONAME( address_of_structure )
```  
  
### <a name="remarks"></a>備註  
 例如:   
  
 [!code-cpp[NVC_ATL_Utilities # 128](../../atl/codesnippet/cpp/string-conversion-macros_1.cpp)]  
  
 以及：  
  
 [!code-cpp[NVC_ATL_Utilities # 129](../../atl/codesnippet/cpp/string-conversion-macros_2.cpp)]  
  
 巨集名稱，來源結構中的字串類型會在左邊 (比方說， **A**)，且目的地結構中的字串類型在右側 (比方說， **W**)。 **A** stands for **LPSTR**, **OLE** stands for `LPOLESTR`, **T** stands for `LPTSTR`, and **W** stands for `LPWSTR`.  
  
 因此，`DEVMODEA2W`複本`DEVMODE`結構和**LPSTR**字串至`DEVMODE`結構和`LPWSTR`字串`TEXTMETRICOLE2T`複本`TEXTMETRIC`結構和`LPOLESTR`字串到`TEXTMETRIC`結構和`LPTSTR`字串，等等。  
  
 轉換中的兩個字串`DEVMODE`結構是裝置名稱 ( **Devmode**) 和表單名稱 ( **dmFormName**)。 `DEVMODE`字串轉換巨集也會更新的結構大小 ( **dmSize**)。  
  
 轉換中的四個字串`TEXTMETRIC`結構是第一個字元 ( **tmFirstChar**)，最後一個字元 ( **tmLastChar**)，預設的字元 ( **tmDefaultChar**)，和符號字元 ( **tmBreakChar**)。  
  
 行為`DEVMODE`和`TEXTMETRIC`字串轉換巨集取決於編譯器中的指示詞效果，如果有的話。 如果來源與目的類型相同，則不會發生轉換。 編譯器指示詞變更**T**和**OLE** ，如下所示︰  
  
|作用中的編譯器指示詞|T 變為|OLE 變為|  
|----------------------------------|---------------|-----------------|  
|無|**A**|**W**|  
|**_UNICODE**|**W**|**W**|  
|**OLE2ANSI**|**A**|**A**|  
|**_UNICODE**和**OLE2ANSI**|**W**|**A**|  
  
 下表列出`DEVMODE`和`TEXTMETRIC`字串轉換巨集。  
  
### <a name="devmode-and-textmetric-string-conversion-macros"></a>DEVMODE 和 TEXTMETRIC 字串轉換巨集  
  
|||  
|-|-|  
|`DEVMODEA2W`|`TEXTMETRICA2W`|  
|`DEVMODEOLE2T`|`TEXTMETRICOLE2T`|  
|`DEVMODET2OLE`|`TEXTMETRICT2OLE`|  
|`DEVMODEW2A`|`TEXTMETRICW2A`|  
  
## <a name="see-also"></a>另請參閱  
 [巨集](../../atl/reference/atl-macros.md)


