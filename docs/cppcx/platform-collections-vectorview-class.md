---
title: "Platform::Collections::VectorView 類別 |Microsoft 文件"
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- COLLECTION/Platform::Collections::VectorView::VectorView
- COLLECTION/Platform::Collections::VectorView::First
- COLLECTION/Platform::Collections::VectorView::GetAt
- COLLECTION/Platform::Collections::VectorView::GetMany
- COLLECTION/Platform::Collections::VectorView::IndexOf
- COLLECTION/Platform::Collections::VectorView::Size
dev_langs: C++
helpviewer_keywords: VectorView Class
ms.assetid: 05cd461d-dce7-49d3-b0e7-2e5c78ed8192
caps.latest.revision: "8"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8ef351759814ee03b54160cac2340eafd304d5f3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="platformcollectionsvectorview-class"></a>Platform::Collections::VectorView 類別
代表物件之循序集合的唯讀檢視，這些物件可透過索引加以個別存取。 集合中每個物件的類型，由樣板參數指定。  
  
## <a name="syntax"></a>語法  
  
```  
template <typename T, typename E>  
   ref class VectorView sealed;  
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 `VectorView` 物件中包含的元素類型。  
  
 `E`  
 指定二元述詞，以測試是否與 `T`型別的值相等。 預設值是 `std::equal_to<T>`。  
  
### <a name="remarks"></a>備註  
 `VectorView`類別會實作[Windows::Foundation::Collections::IVectorView\<T >](http://go.microsoft.com/fwlink/p/?LinkId=262411)介面，也支援標準樣板程式庫迭代器。  
  
### <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[Vectorview:: Vectorview](#ctor)|初始化 VectorView 類別的新執行個體。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[Vectorview:: First](#first)|傳回迭代器，指定 VectorView 中的第一個項目。|  
|[Vectorview:: Getat](#getat)|擷取由指定之索引所表示的目前 VectorView 項目。|  
|[Vectorview:: Getmany](#getmany)|由指定的索引處開始，從目前 VectorView 擷取一連串項目。|  
|[Vectorview:: Indexof](#indexof)|在目前 VectorView 中搜尋指定的項目，如果找到，則傳回項目的索引。|  
|[Vectorview:: Size](#size)|傳回目前 VectorView 物件中的項目數。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `VectorView`  
  
### <a name="requirements"></a>需求  
 **標頭：** collection.h  
  
 **命名空間：** Platform::Collections  

## <a name="first"></a>Vectorview:: First 方法
傳回迭代器，指定 VectorView 中的第一個項目。  
  
### <a name="syntax"></a>語法  
  
```  
  
virtual Windows::Foundation::Collections::IIterator<T>^   
   First();  
```  
  
### <a name="return-value"></a>傳回值  
 指定 VectorView 中第一個項目的迭代器。  
  
### <a name="remarks"></a>備註  
 若要保留 first （） 所傳回的迭代器的簡便方法是宣告的變數指派傳回值**自動**型别推斷關鍵字。 例如，`auto x = myVectorView->First();`。  
  


## <a name="getat"></a>Vectorview:: Getat 方法
擷取由指定之索引所表示的目前 VectorView 項目。  
  
### <a name="syntax"></a>語法  
  
```  
  
T GetAt(  
   UInt32 index  
);  
```  
  
### <a name="parameters"></a>參數  
 `index`  
 以零起始、不帶正負號的整數，在 VectorView 物件中指定特別項目。  
  
### <a name="return-value"></a>傳回值  
 `index` 參數指定的項目。 VectorView 範本參數所指定的項目類型*T*。  
  


## <a name="getmany"></a>Vectorview:: Getmany 方法
由指定的索引處開始，從目前 VectorView 擷取一連串項目。  
  
### <a name="syntax"></a>語法  
  
```  
  
virtual unsigned int GetMany(  
   unsigned int startIndex,   
   ::Platform::WriteOnlyArray<T>^ dest  
);  
```  
  
### <a name="parameters"></a>參數  
 `startIndex`  
 要擷取之開始項目以零為起始的索引。  
  
 `dest`  
 這項作業完成時，會開始於指定的項目之項目的陣列`startIndex`並在 VectorView 中的最後一個元素結束。  
  
### <a name="return-value"></a>傳回值  
 擷取的項目數目。  
  


## <a name="indexof"></a>Vectorview:: Indexof 方法
在目前 VectorView 中搜尋指定的項目，如果找到，則傳回項目的索引。  
  
### <a name="syntax"></a>語法  
  
```  
  
virtual bool IndexOf(  
   T value,  
   unsigned int* index  
);  
```  
  
### <a name="parameters"></a>參數  
 `value`  
 要尋找的項目。  
  
 `index`  
 如果找到參數 `value`，則為項目以零起始的索引，否則為 0。  
  
 如果項目是 VectorView 的第一個項目或找不到項目，則 `index` 參數為 0。 如果傳回值為 `true`，表示找到符合項目，並且是第一個項目，否則表示找不到項目。  
  
### <a name="return-value"></a>傳回值  
 如果找到指定的項目則為 `true`，否則為 `false`。  
  


## <a name="size"></a>Vectorview:: Size 方法
傳回目前 VectorView 物件中的項目數。  
  
### <a name="syntax"></a>語法  
  
```  
  
virtual property unsigned int Size;  
```  
  
### <a name="return-value"></a>傳回值  
 目前 VectorView 中的項目數。  
  


## <a name="ctor"></a>Vectorview:: Vectorview 建構函式
初始化 VectorView 類別的新執行個體。  
  
### <a name="syntax"></a>語法  
  
```  
VectorView();  
explicit VectorView(  
   UInt32 size  
);  
VectorView(  
   UInt32 size,  
   T value  
);  
explicit VectorView(  
   const ::std::vector<T>& v  
);  
explicit VectorView(  
   ::std::vector<T>&& v  
);  
VectorView(  
   const T * ptr,  
   UInt32 size  
);  
  
template <  
   size_t N  
>  
explicit VectorView(  
   const T (&arr)[N]  
);  
  
template <  
   size_t N  
>  
explicit VectorView(  
   const ::std::array<T,  
   N>& a  
);  
  
explicit VectorView(  
   const ::Platform::Array<T>^ arr  
);  
  
template <  
   typename InIt  
>  
VectorView(  
   InItfirst,  
   InItlast  
);  
  
VectorView(  
   std::initializer_list<T> il  
);  
```  
  
### <a name="parameters"></a>參數  
 `InIt`  
 用來初始化目前 VectorView 的物件集合類型。  
  
 il  
 A [std:: initializer_list](../standard-library/initializer-list-class.md)其元素將用來初始化 VectorView。  
  
 `N`  
 用來初始化目前 VectorView 之物件集合中的項目數。  
  
 `size`  
 VectorView 中的項目數。  
  
 `value`  
 用來初始化目前 VectorView 中各個項目的值。  
  
 `v`  
 [Lvalues 和 Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md)至[std:: vector](../standard-library/vector-class.md)用來初始化目前 VectorView。  
  
 `ptr`  
 用來初始化目前 VectorView 之 `std::vector` 的指標。  
  
 `arr`  
 A [platform:: array](../cppcx/platform-array-class.md)用來初始化目前 VectorView 的物件。  
  
 `a`  
 A [std:: array](../standard-library/array-class-stl.md)用來初始化目前 VectorView 的物件。  
  
 `first`  
 用來初始化目前 VectorView 之物件序列中的第一個項目。 型別`first`會藉由傳遞*完美地轉送*。 如需詳細資訊，請參閱[右值參考宣告子：&&](../cpp/rvalue-reference-declarator-amp-amp.md)。  
  
 `last`  
 用來初始化目前 VectorView 之物件序列中的最後一個項目。 型別`last`會藉由傳遞*完美地轉送*。 如需詳細資訊，請參閱[右值參考宣告子：&&](../cpp/rvalue-reference-declarator-amp-amp.md)。  
  


  
## <a name="see-also"></a>請參閱  
 [Platform 命名空間](platform-namespace-c-cx.md)   
 [在 c + + 中建立 Windows 執行階段元件](/MicrosoftDocs/windows-uwp/blob/docs/windows-apps-src/winrt-components/creating-windows-runtime-components-in-cpp.md)