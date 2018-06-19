---
title: ATL 集合類別 |Microsoft 文件
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
ms.openlocfilehash: 4594b87f07cd4d89937ba640d9a04aeacf2ef866
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32359826"
---
# <a name="atl-collection-classes"></a>ATL 集合類別
ATL 提供許多類別來儲存和存取資料。 您決定使用哪一個類別取決於許多因素，包括：  
  
-   要儲存的資料量  
  
-   存取資料的效率和效能  
  
-   依據索引或索引鍵存取資料的能力  
  
-   如何排序資料  
  
-   個人的喜好設定  
  
## <a name="small-collection-classes"></a>小型集合類別  
 ATL 提供下列的陣列類別處理小量的物件。 但是，這些類別的限制，而且適用於內部 atl 不建議它們使用您程式中。  
  
|類別|資料存放區的類型|  
|-----------|--------------------------|  
|[CSimpleArray](../atl/reference/csimplearray-class.md)|實作處理少量物件的陣列類別。|  
|[CSimpleMap](../atl/reference/csimplemap-class.md)|實作處理物件的小量的對應類別。|  
  
## <a name="general-purpose-collection-classes"></a>一般用途的集合類別  
 下列類別實作陣列、 清單和對應，並提供一般用途的集合類別：  
  
|類別|資料存放區的類型|  
|-----------|--------------------------|  
|[CAtlArray](../atl/reference/catlarray-class.md)|實作陣列。|  
|[CAtlList](../atl/reference/catllist-class.md)|實作清單。|  
|[CAtlMap](../atl/reference/catlmap-class.md)|實作對應的結構，讓資料可以參考索引鍵或值。|  
|[CRBMap](../atl/reference/crbmap-class.md)|實作對應結構使用紅黑演算法。|  
|[CRBMultiMap](../atl/reference/crbmultimap-class.md)|實作紅黑多重對應的結構。|  
  
 這些類別將會落入偵錯組建中使用時的許多程式設計錯誤，但為了效能，這些檢查不會執行在零售組建中。  
  
## <a name="specialized-collection-classes"></a>特製化的集合類別  
 也提供更具特製化的集合類別，來管理記憶體的指標和介面指標：  
  
|類別|用途|  
|-----------|-------------|  
|[CAutoPtrArray](../atl/reference/cautoptrarray-class.md)|建構智慧型指標的陣列時，請提供有效的方法。|  
|[CAutoPtrList](../atl/reference/cautoptrlist-class.md)|建構的智慧型指標清單時，請提供有效的方法。|  
|[CComUnkArray](../atl/reference/ccomunkarray-class.md)|存放區`IUnknown`指標，並且可當做參數使用[IConnectionPointImpl](../atl/reference/iconnectionpointimpl-class.md)範本類別。|  
|[CHeapPtrList](../atl/reference/cheapptrlist-class.md)|建構堆積指標清單時，請提供有效的方法。|  
|[CInterfaceArray](../atl/reference/cinterfacearray-class.md)|建構 COM 介面指標的陣列時，請提供有效的方法。|  
|[CInterfaceList](../atl/reference/cinterfacelist-class.md)|建構 COM 介面指標的清單時，請提供有效的方法。|  
  
## <a name="choosing-a-collection-class"></a>選擇集合類別  
 下表所示，每個可用的集合類別會提供不同效能特性。  
  
-   資料行 2 和 3 描述每個類別的排序和存取特性。 在下表中，「已排序」一詞是指項目的插入和刪除順序決定其在集合中的順序；而不是指項目依其內容排序。 「已編製索引」一詞是指集合中的項目可由整數索引擷取，就像是一般陣列中的項目。  
  
-   欄 4 和 5 描述每個類別的效能。 在需要多次插入集合的應用程式中，插入速度可能特別重要；至於其他應用程式，查閱速度可能比較重要。  
  
-   欄 6 描述每個圖形是否允許重複的項目。  
  
-   完成作業，且集合中的項目數所需的時間之間的關聯性是以表示指定的集合類別作業的效能。 作業花費的時間量的增加而呈線性成長所述的項目增加而增加數字做為 o （n） 演算法。 相反地，作業花費一段時間，從而越來越不為的項目增加而增加數字會描述為 O (記錄 n) 演算法。 因此，在效能方面，O (記錄 n) 演算法優於越來越多做數目的項目增加為 o （n） 演算法。  
  
### <a name="collection-shape-features"></a>集合圖形功能  
  
|圖形|排序|編製索引|插入<br /><br /> 項目|搜尋<br /><br /> 指定的項目|重複項目<br /><br /> 項目|  
|-----------|--------------|--------------|---------------------------|--------------------------------------|-----------------------------|  
|清單|[是]|否|Fast （常數時間）|緩慢 o （n）|[是]|  
|陣列|[是]|依 int （常數時間）|但如果在結尾插入，可以在哪一個案例的常數時間緩慢 o （n）|緩慢 o （n）|[是]|  
|對應|否|依索引鍵 （常數時間）|Fast （常數時間）|Fast （常數時間）|否 (索引鍵) 是 (值)|  
|紅黑對應|是 （依索引鍵）|依索引鍵 O (記錄 n)|快速 O (記錄 n)|快速 O (記錄 n)|否|  
|紅黑多重對應|是 （依索引鍵）|依索引鍵 O(log n) （每個索引鍵的多個值）|快速 O (記錄 n)|快速 O (記錄 n)|是 （每個索引鍵的多個值）|  
  
## <a name="using-ctraits-objects"></a>使用 CTraits 物件  
 ATL 集合類別可以用來儲存各種不同的使用者定義資料類型，它可用來覆寫重要的功能，例如比較。 這是利用 CTraits 類別來達成。  
  
 CTraits 類別是類似，但 MFC 集合類別 helper 函式; 比更有彈性請參閱[集合類別 Helper](../mfc/reference/collection-class-helpers.md)如需詳細資訊。  
  
 當建構您的集合類別，您可以指定 CTraits 類別的選擇。 此類別所包含的程式碼，將會執行作業，例如組成的集合類別的方法呼叫時的比較。 比方說，如果您的清單物件會包含您的使用者定義的結構，您可能想要重新定義等號比較測試，只比較 特定的成員變數。 如此一來，清單物件的 Find 方法會以更有用的方式。  
  
## <a name="example"></a>範例  
  
### <a name="code"></a>程式碼  
 [!code-cpp[NVC_ATL_Utilities#112](../atl/codesnippet/cpp/atl-collection-classes_1.cpp)]  
  
## <a name="comments"></a>註解  
 如需 CTraits 類別的清單，請參閱[集合類別](../atl/collection-classes.md)。  
  
 下圖顯示 CTraits 類別的類別階層。  
  
 ![集合類別的特性階層架構](../atl/media/vctraitscollectionclasseshierarchy.gif "vctraitscollectionclasseshierarchy")  
  
## <a name="collection-classes-samples"></a>集合類別的範例  
 下列範例會示範集合類別：  
  
-   [MMXSwarm 範例](../visual-cpp-samples.md)  
  
-   [DynamicConsumer 範例](../visual-cpp-samples.md)  
  
-   [UpdatePV 範例](../visual-cpp-samples.md)  
  
-   [跑馬燈範例](../visual-cpp-samples.md)  
  
## <a name="see-also"></a>另請參閱  
 [概念](../atl/active-template-library-atl-concepts.md)   
 [集合類別](../atl/collection-classes.md)

