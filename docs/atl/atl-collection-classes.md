---
title: ATL 集合類別總覽
ms.date: 11/19/2018
helpviewer_keywords:
- DestructElements function
- collection classes, choosing
- ConstructElements function
- SerializeElements function
- traits classes
- collection classes, about collection classes
- CTraits classes
- collection classes
ms.assetid: 4d619d46-5b4e-41dd-b9fd-e86b1fbc00b5
ms.openlocfilehash: 039af388a3713540c6ba7d39e8b639cf83d291ff
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2020
ms.locfileid: "90040856"
---
# <a name="atl-collection-classes"></a>ATL 集合類別

ATL 提供許多類別來儲存及存取資料。 您決定使用哪一種類別取決於數個因素，包括：

- 要儲存的資料量

- 存取資料的效率與效能

- 依索引或依索引鍵存取資料的能力

- 如何排序資料

- 個人喜好設定

## <a name="small-collection-classes"></a>小型集合類別

ATL 提供下列陣列類別來處理少量的物件。 不過，這些類別會受到限制，而且是設計成由 ATL 在內部使用。 不建議您在程式中使用它們。

|類別|資料儲存體的類型|
|-----------|--------------------------|
|[CSimpleArray](../atl/reference/csimplearray-class.md)|執行陣列類別以處理少量的物件。|
|[CSimpleMap](../atl/reference/csimplemap-class.md)|實處理少量物件的對應類別。|

## <a name="general-purpose-collection-classes"></a>一般用途集合類別

下列類別會執行陣列、清單和對應，並以一般用途的集合類別形式提供：

|類別|資料儲存體的類型|
|-----------|--------------------------|
|[CAtlArray](../atl/reference/catlarray-class.md)|實行陣列。|
|[CAtlList](../atl/reference/catllist-class.md)|實行清單。|
|[CAtlMap](../atl/reference/catlmap-class.md)|會執行對應結構，讓資料可以依索引鍵或值來參考。|
|[CRBMap](../atl/reference/crbmap-class.md)|使用紅黑色演算法來執行對應結構。|
|[CRBMultiMap](../atl/reference/crbmultimap-class.md)|實 multimapping 結構的紅色。|

在偵錯工具中使用時，這些類別會攔截許多程式設計錯誤，但為了提高效能，這些檢查將不會在零售組建中執行。

## <a name="specialized-collection-classes"></a>特製化集合類別

也提供更特製化的集合類別來管理記憶體指標和介面指標：

|類別|目的|
|-----------|-------------|
|[CAutoPtrArray](../atl/reference/cautoptrarray-class.md)|提供在建立智慧型指標的陣列時有用的方法。|
|[CAutoPtrList](../atl/reference/cautoptrlist-class.md)|提供當您建立智慧型指標清單時有用的方法。|
|[CComUnkArray](../atl/reference/ccomunkarray-class.md)|儲存 `IUnknown` 指標，且設計用來作為 [IConnectionPointImpl](../atl/reference/iconnectionpointimpl-class.md) 範本類別的參數。|
|[CHeapPtrList](../atl/reference/cheapptrlist-class.md)|提供在建立堆積指標清單時有用的方法。|
|[CInterfaceArray](../atl/reference/cinterfacearray-class.md)|提供在建立 COM 介面指標的陣列時有用的方法。|
|[CInterfaceList](../atl/reference/cinterfacelist-class.md)|提供在建立 COM 介面指標清單時有用的方法。|

## <a name="choosing-a-collection-class"></a>選擇集合類別

每個可用的集合類別都提供不同的效能特性，如下表所示。

- 資料行2和3描述每個類別的順序和存取特性。 在下表中，「已排序」一詞是指項目的插入和刪除順序決定其在集合中的順序；而不是指項目依其內容排序。 「已編製索引」一詞是指集合中的項目可由整數索引擷取，就像是一般陣列中的項目。

- 資料行4和5描述每個類別的效能。 在需要多次插入集合的應用程式中，插入速度可能特別重要；至於其他應用程式，查閱速度可能比較重要。

- 欄 6 描述每個圖形是否允許重複的項目。

- 給定集合類別作業的效能會以完成作業所需的時間和集合中的專案數來表示。 作業所花費的時間量，會隨著元素數目的增加而以線性方式增加， (n) 演算法。 相反地，如果作業所花費的時間較少，而增加的專案數目，則會以 O (log n) 演算法來描述。 因此，在效能方面，O (記錄 n) 演算法優於 O (n) 演算法會隨著元素數目的增加而增加。

### <a name="collection-shape-features"></a>集合圖形功能

|形狀|訂購時間|索引|插入<br /><br /> element|搜尋<br /><br /> 指定的元素|重複<br /><br /> 元素|
|-----------|--------------|--------------|---------------------------|--------------------------------------|-----------------------------|
|清單|是|否|快速 (常數時間) |慢速 O (n) |是|
|Array|是|依整數 (常數時間) |慢 O (n) 例外，除非在結尾插入，在此情況下會有常數時間|慢速 O (n) |是|
|對應|否|依 key (常數 time) |快速 (常數時間) |快速 (常數時間) |否 (索引鍵) 是 (值)|
|紅色-黑色地圖|是 (按鍵) |依金鑰 O (記錄 n) |快速 O (記錄 n) |快速 O (記錄 n) |否|
|紅-黑色 Multimap|是 (按鍵) |依金鑰 O (記錄 n)  (每個索引鍵有多個值) |快速 O (記錄 n) |快速 O (記錄 n) |是 (每個索引鍵有多個值) |

## <a name="using-ctraits-objects"></a>使用 CTraits 物件

當 ATL 集合類別可用來儲存廣泛的使用者定義資料類型時，能夠覆寫重要的函式（例如比較）可能會很有用。 這是使用 CTraits 類別來達成。

CTraits 類別類似于 MFC 集合類別 helper 函式，但是更有彈性;如需詳細資訊，請參閱 [集合類別](../mfc/reference/collection-class-helpers.md) 協助程式。

當您建立集合類別時，您可以選擇指定 CTraits 類別。 這個類別包含的程式碼會在由組成集合類別的其他方法呼叫時，執行像是比較的作業。 例如，如果您的清單物件包含您自己的使用者定義結構，您可能會想要將相等測試重新定義為只比較特定的成員變數。 如此一來，清單物件的 Find 方法會以更實用的方式運作。

## <a name="example"></a>範例

### <a name="code"></a>程式碼

[!code-cpp[NVC_ATL_Utilities#112](../atl/codesnippet/cpp/atl-collection-classes_1.cpp)]

## <a name="comments"></a>註解

如需 CTraits 類別的清單，請參閱 [集合類別](../atl/collection-classes.md)。

下圖顯示 CTraits 類別的類別階層架構。

![集合類別的特性階層架構](../atl/media/vctraitscollectionclasseshierarchy.gif "集合類別的特性階層架構")

## <a name="collection-classes-samples"></a>集合類別範例

下列範例示範集合類別：

- [MMXSwarm 範例](../overview/visual-cpp-samples.md)

- [DynamicConsumer 範例](../overview/visual-cpp-samples.md)

- [UpdatePV 範例](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV)

- [天棚範例](../overview/visual-cpp-samples.md)

## <a name="see-also"></a>另請參閱

[概念](../atl/active-template-library-atl-concepts.md)<br/>
[集合類別](../atl/collection-classes.md)
