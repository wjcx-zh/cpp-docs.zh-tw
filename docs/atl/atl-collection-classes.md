---
title: ATL 集合類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 18369de567c830973bef26d886d5a2048bb0109f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46048912"
---
# <a name="atl-collection-classes"></a>ATL 集合類別

ATL 提供許多類別來儲存和存取資料。 您決定使用哪一個類別取決於許多因素，包括：

- 要儲存的資料量

- 在存取資料的效能與效率

- 依據索引或索引鍵存取資料的能力

- 如何排序資料

- 個人的喜好設定

## <a name="small-collection-classes"></a>小型集合類別

ATL 提供下列陣列類別來處理數量不多的物件。 不過，這些類別都會限制，而且主要是供內部 ATL 不建議您使用它們在程式中。

|類別|資料儲存體類型|
|-----------|--------------------------|
|[CSimpleArray](../atl/reference/csimplearray-class.md)|實作處理少量物件的陣列類別。|
|[CSimpleMap](../atl/reference/csimplemap-class.md)|實作對應的類別處理小量的物件。|

## <a name="general-purpose-collection-classes"></a>一般用途的集合類別

下列類別實作陣列、 清單和對應，並提供一般用途的集合類別：

|類別|資料儲存體類型|
|-----------|--------------------------|
|[CAtlArray](../atl/reference/catlarray-class.md)|實作一個陣列。|
|[CAtlList](../atl/reference/catllist-class.md)|實作清單。|
|[CAtlMap](../atl/reference/catlmap-class.md)|實作對應的結構，藉此參考資料，由索引鍵或值。|
|[CRBMap](../atl/reference/crbmap-class.md)|實作使用紅黑演算法對應結構。|
|[CRBMultiMap](../atl/reference/crbmultimap-class.md)|實作紅黑多重對應的結構。|

這些類別會攔截在偵錯組建中使用時的許多程式設計錯誤，但為了效能，這些檢查不會執行在零售組建中。

## <a name="specialized-collection-classes"></a>特製化的集合類別

管理記憶體的指標和介面指標，也會提供更具特製化的集合類別：

|類別|用途|
|-----------|-------------|
|[CAutoPtrArray](../atl/reference/cautoptrarray-class.md)|建構的智慧型指標陣列時，請提供有效的方法。|
|[CAutoPtrList](../atl/reference/cautoptrlist-class.md)|建構的智慧型指標清單時，請提供有效的方法。|
|[CComUnkArray](../atl/reference/ccomunkarray-class.md)|存放區`IUnknown`指標，旨在用於做為參數[IConnectionPointImpl](../atl/reference/iconnectionpointimpl-class.md)範本類別。|
|[CHeapPtrList](../atl/reference/cheapptrlist-class.md)|建構一份堆積指標時，請提供有效的方法。|
|[CInterfaceArray](../atl/reference/cinterfacearray-class.md)|建構 COM 介面指標的陣列時，請提供有效的方法。|
|[CInterfaceList](../atl/reference/cinterfacelist-class.md)|建構 COM 介面指標的清單時，請提供有效的方法。|

## <a name="choosing-a-collection-class"></a>選擇集合類別

下表所示，每個可用性集合類別會提供不同的效能特性。

- 資料行 2 和 3 描述每個類別的順序，並存取特性。 在下表中，「已排序」一詞是指項目的插入和刪除順序決定其在集合中的順序；而不是指項目依其內容排序。 「已編製索引」一詞是指集合中的項目可由整數索引擷取，就像是一般陣列中的項目。

- 欄 4 和 5 描述每個類別的效能。 在需要多次插入集合的應用程式中，插入速度可能特別重要；至於其他應用程式，查閱速度可能比較重要。

- 欄 6 描述每個圖形是否允許重複的項目。

- 若要完成此作業和集合中的項目數所需的時間之間的關聯性是以表示指定的集合類別作業的效能。 作業花費的時間量，會呈線性增加所述的項目數目的增加數目是做為 o （n） 演算法。 相反地，作業花費一段時間，從而減少項目數目的增加數字會描述為 O (log n) 演算法。 因此，在效能方面，O (log n) 演算法的表現優於 o （n） 演算法，越來越多如的項目數目的增加數目。

### <a name="collection-shape-features"></a>集合圖形功能

|圖形|排序|編製索引|插入<br /><br /> 項目|搜尋<br /><br /> 指定的項目|重複項目<br /><br /> 項目|
|-----------|--------------|--------------|---------------------------|--------------------------------------|-----------------------------|
|清單|是|否|快速 （常數時間）|緩慢 o （n)|是|
|陣列|是|依 int （常數時間）|但如果在插入結束時，在哪一個案例的常數時間緩慢 o （n）|緩慢 o （n)|是|
|對應|否|依索引鍵 （常數時間）|快速 （常數時間）|快速 （常數時間）|否 (索引鍵) 是 (值)|
|紅黑對應|是 （藉由索引鍵）|依索引鍵 O (log n)|快速 O (log n)|快速 O (log n)|否|
|紅黑 Multimap|是 （藉由索引鍵）|依索引鍵 O(log n) （每個索引鍵的多個值）|快速 O (log n)|快速 O (log n)|是 （每個索引鍵的多個值）|

## <a name="using-ctraits-objects"></a>使用 CTraits 物件

ATL 集合類別可以用來儲存各種不同的使用者定義資料類型，它可以是相當實用，能覆寫重要的功能，例如比較。 這是使用 CTraits 類別所達成的。

CTraits 類別是類似，但比 MFC 集合類別 helper 函式; 更有彈性請參閱[集合類別 Helper](../mfc/reference/collection-class-helpers.md)如需詳細資訊。

當建構您的集合類別時，您可以選擇指定 CTraits 類別。 此類別會包含將執行作業，例如比較時所組成的集合類別的方法呼叫的程式碼。 例如，如果您的清單物件中包含您自己的使用者定義結構，您可能想要重新定義等號比較測試，只比較 特定的成員變數。 如此一來，清單物件的 Find 方法會更有用的方式運作。

## <a name="example"></a>範例

### <a name="code"></a>程式碼

[!code-cpp[NVC_ATL_Utilities#112](../atl/codesnippet/cpp/atl-collection-classes_1.cpp)]

## <a name="comments"></a>註解

如需 CTraits 類別的清單，請參閱 <<c0> [ 集合類別](../atl/collection-classes.md)。

下圖顯示 CTraits 類別的類別階層。

![集合類別特性階層架構](../atl/media/vctraitscollectionclasseshierarchy.gif "vctraitscollectionclasseshierarchy")

## <a name="collection-classes-samples"></a>集合類別的範例

下列範例會示範集合類別：

- [MMXSwarm 範例](../visual-cpp-samples.md)

- [DynamicConsumer 範例](../visual-cpp-samples.md)

- [UpdatePV 範例](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV)

- [跑馬燈範例](../visual-cpp-samples.md)

## <a name="see-also"></a>另請參閱

[概念](../atl/active-template-library-atl-concepts.md)<br/>
[集合類別](../atl/collection-classes.md)

