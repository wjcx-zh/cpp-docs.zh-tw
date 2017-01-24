---
title: "array 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "amp/Concurrency::array"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "array 類別"
ms.assetid: 0832b6c1-40f0-421d-9104-6b1baa0c63a7
caps.latest.revision: 31
caps.handback.revision: 31
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# array 類別
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

表示用來將資料移至對應的資料容器。  
  
## <a name="syntax"></a>語法  
  
```  
template <
    typename value_type,  
    int _Rank  
>  
friend class array;  
```  
  
#### <a name="parameters"></a>參數  
 `value_type`  
 項目類型的資料。  
  
 `_Rank`  
 陣列的陣序規範。  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[array:: array 建構函式](#array__array_constructor)|初始化 `array` 類別的新執行個體。|  
|[陣列:: ~ array 解構函式](#array___dtorarray_destructor)|終結 `array` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[array:: copy_to 方法](#array__copy_to_method)|將陣列的內容複製到另一個陣列。|  
|[array:: data 方法](#array__data_method)|傳回陣列的未經處理資料的指標。|  
|[array:: get_accelerator_view 方法](#array__get_accelerator_view_method)|傳回 [accelerator_view](../../../parallel/amp/reference/accelerator-view-class.md) 物件，代表陣列的配置位置。 這個屬性可以只在 CPU 上存取。|  
|[array:: get_associated_accelerator_view 方法](#array__get_associated_accelerator_view_method)|取得第二個 [accelerator_view](../../../parallel/amp/reference/accelerator-view-class.md) 臨時的建構函式呼叫來具現化時，做為參數傳遞的物件 [陣列](../../../parallel/amp/reference/array-class.md) 物件。|  
|[array:: get_cpu_access_type 方法](#array__get_cpu_access_type_method)|傳回 [access_type](access_type%20Enumeration.md) 的陣列。 這個方法可以只在 CPU 上存取。|  
|[array:: get_extent 方法](#array__get_extent_method)|傳回 [範圍](../../../parallel/amp/reference/extent-class-cpp-amp.md) 物件的陣列。|  
|[array:: reinterpret_as 方法](#array__reinterpret_as_method)|傳回一維陣列，包含在所有項目 `array` 物件。|  
|[array:: section 方法](#array__section_method)|傳回的子區段 [陣列](../../../parallel/amp/reference/array-class.md) 物件在指定的來源，並選擇性地，具有指定的範圍。|  
|[array:: view_as 方法](#array__view_as_method)|傳回 [array_view](../../../parallel/amp/reference/array-view-class.md) 建構從物件 `array` 物件。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|說明|  
|----------|-----------------|  
|[array:: operator std:: vector&lt;value_type&gt; 運算子](#array__operator_std__vector_lt__value_type_gt__operator)|使用 `copy(*this, vector)` 來隱含地將陣列轉換成 std::[向量](../../../standard-library/vector-class.md) 物件。|  
|[array:: operator （) 運算子](#array__operator___operator)|傳回參數所指定的項目值。|  
|[array:: operator [] 運算子](#array__operator_at_operator)|傳回指定索引處的項目。|  
|[array:: operator = 運算子](#array__operator_eq_operator)|將指定的內容複製 `array` 到這裡的物件。|  
  
### <a name="public-constants"></a>公用常數  
  
|名稱|說明|  
|----------|-----------------|  
|[array:: rank 常數](#array__rank_constant)|儲存陣列的陣序規範。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|[array:: accelerator_view 資料成員](#array__accelerator_view_data_member)|取得 [accelerator_view](../../../parallel/amp/reference/accelerator-view-class.md) 物件，代表陣列的配置位置。 這個屬性可以只在 CPU 上存取。|  
|[array:: associated_accelerator_view 資料成員](#array__associated_accelerator_view_data_member)|取得第二個 [accelerator_view](../../../parallel/amp/reference/accelerator-view-class.md) 臨時的建構函式呼叫來具現化時，做為參數傳遞的物件 [陣列](../../../parallel/amp/reference/array-class.md) 物件。|  
|[array:: cpu_access_type 資料成員](#array__cpu_access_type_data_member)|取得 [access_type](access_type%20Enumeration.md) 表示 CPU 存取陣列的儲存體的方式。|  
|[array:: extent 資料成員](#array__extent_data_member)|取得定義陣列形狀的程度。|  
  
## <a name="remarks"></a>備註  
 型別 `array<T,N>` 代表密集及一般 （不不規則） *N*-位於特定的位置，例如快速鍵或 CPU 的二維陣列。 陣列中元素的資料型別是 `T`, ，該值必須與目標加速器相容的型別。 雖然順位、 `N`, ，(的陣列以靜態方式判斷類型的一部分，陣列的範圍取決於執行階段，並使用類別來表示 `extent<N>`。  
  
 陣列可以有任意數目的維度，雖然有些功能專門用於 `array` 排名一、 兩個與三個物件。 如果您省略維度引數，預設值為 1。  
  
 陣列資料是連續配置在記憶體中。 不同的其中一個最小顯著性的維度中的項目會在記憶體中相鄰的。  
  
 陣列是以邏輯方式被視為實值型別，因為當陣列複製到另一個陣列，要執行的深層複本。 這兩個陣列永遠不會指向相同的資料。  
  
  `array<T,N>` 類型用在許多案例︰  
  
-   為資料容器，可用於計算加速器。  
  
-   為資料容器，以保留在主機 CPU 記憶體 （也可用於從其他陣列複製）。  
  
-   為暫存物件做為主機對裝置複本中的快速媒介。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `array`  
  
## <a name="requirements"></a>需求  
 **標頭︰** amp.h  
  
 **命名空間：** 並行  
  
##  <a name="a-namearraydtorarraydestructora-arrayarray-destructor"></a><a name="array___dtorarray_destructor"></a>  陣列:: ~ array 解構函式  
 終結 `array` 物件。  
  
```  
~array() restrict(cpu);
```  
  
##  <a name="a-namearrayacceleratorviewdatamembera-arrayacceleratorview-data-member"></a><a name="array__accelerator_view_data_member"></a>  array:: accelerator_view 資料成員  
 取得 [accelerator_view](../../../parallel/amp/reference/accelerator-view-class.md) 物件，代表陣列的配置位置。 這個屬性可以只在 CPU 上存取。  
  
```  
__declspec(property(get= get_accelerator_view)) Concurrency::accelerator_view accelerator_view;  
```  
  
##  <a name="a-namearrayarrayconstructora-arrayarray-constructor"></a><a name="array__array_constructor"></a>  array:: array 建構函式  
 初始化的新執行個體 [array 類別](../../../parallel/amp/reference/array-class.md)。 沒有預設建構函式的 `array<T,N>`。 只有在 CPU 上執行所有建構函式。 它們無法 Direct3D 目標上執行。  
  
```  
explicit array(
    const Concurrency::extent<_Rank>& _Extent) restrict(cpu);

 
explicit array(
    int _E0) restrict(cpu);

 
explicit array(
    int _E0,  
    int _E1) restrict(cpu);

 
explicit array(
    int _E0,  
    int _E1,  
    int _E2) restrict(cpu);

 
array(
    const Concurrency::extent<_Rank>& _Extent,  
    Concurrency::accelerator_view _Av  
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

 
array(
    int _E0,  
    Concurrency::accelerator_view _Av  
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

 
array(
    int _E0,  
    int _E1,  
    Concurrency::accelerator_view _Av  
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

 
array(
    int _E0,  
    int _E1,  
    int _E2,  
    Concurrency::accelerator_view _Av  
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

 
array(
    const Concurrency::extent<_Rank>& _Extent,  
    Concurrency::accelerator_view _Av,  
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

 
array(
    int _E0,  
    accelerator_view _Av,  
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

 
array(
    int _E0,  
    int _E1,  
    Concurrency::accelerator_view _Av,  
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

 
array(
    int _E0,  
    int _E1,  
    int _E2,  
    Concurrency::accelerator_view _Av,  
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

 
template <
    typename _InputIterator  
>  
array(
    const Concurrency::extent<_Rank>& _Extent, _InputIterator _Src_first, _InputIterator _Src_last) restrict(cpu);

 
template <
    typename _InputIterator  
>  
array(
    const Concurrency::extent<_Rank>& _Extent, _InputIterator _Src_first) restrict(cpu);

 
template <
    typename _InputIterator  
>  
array(
    int _E0, _InputIterator _Src_first, _InputIterator _Src_last) restrict(cpu);

 
template <
    typename _InputIterator  
>  
array(
    int _E0, _InputIterator _Src_first) restrict(cpu);

 
template <
    typename _InputIterator  
>  
array(
    int _E0,  
    int _E1, _InputIterator _Src_first, _InputIterator _Src_last) restrict(cpu);

 
template <
    typename _InputIterator  
>  
array(
    int _E0,  
    int _E1, _InputIterator _Src_first) restrict(cpu);

 
template <
    typename _InputIterator  
>  
array(
    int _E0,  
    int _E1,  
    int _E2, _InputIterator _Src_first, _InputIterator _Src_last) restrict(cpu);

 
template <
    typename _InputIterator  
>  
array(
    int _E0,  
    int _E1,  
    int _E2, _InputIterator _Src_first) restrict(cpu);

 
template <
    typename _InputIterator  
>  
array(
    const Concurrency::extent<_Rank>& _Extent, _InputIterator _Src_first, _InputIterator _Src_last,  
    Concurrency::accelerator_view _Av  
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

 
template <
    typename _InputIterator  
>  
array(
    const Concurrency::extent<_Rank>& _Extent, _InputIterator _Src_first,  
    Concurrency::accelerator_view _Av  
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

 
template <
    typename _InputIterator  
>  
array(
    int _E0, _InputIterator _Src_first, _InputIterator _Src_last,  
    Concurrency::accelerator_view _Av  
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

 
template <
    typename _InputIterator  
>  
array(
    int _E0, _InputIterator _Src_first,  
    Concurrency::accelerator_view _Av  
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

 
template <
    typename _InputIterator  
>  
array(
    int _E0,  
    int _E1, _InputIterator _Src_first, _InputIterator _Src_last,  
    Concurrency::accelerator_view _Av  
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

 
template <
    typename _InputIterator  
>  
array(
    int _E0,  
    int _E1, _InputIterator _Src_first,  
    Concurrency::accelerator_view _Av  
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

 
template <
    typename _InputIterator  
>  
array(
    int _E0,  
    int _E1,  
    int _E2, _InputIterator _Src_first, _InputIterator _Src_last,  
    Concurrency::accelerator_view _Av,  
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

 
template <
    typename _InputIterator  
>  
array(
    int _E0,  
    int _E1,  
    int _E2, _InputIterator _Src_first,  
    Concurrency::accelerator_view _Av  
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

 
template <
    typename _InputIterator  
>  
array(
    const Concurrency::extent<_Rank>& _Extent, _InputIterator _Src_first, _InputIterator _Src_last,  
    Concurrency::accelerator_view _Av,  
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

 
template <
    typename _InputIterator  
>  
array(
    const Concurrency::extent<_Rank>& _Extent, _InputIterator _Src_first,  
    Concurrency::accelerator_view _Av,  
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

 
template <
    typename _InputIterator  
>  
array(
    int _E0, _InputIterator _Src_first, _InputIterator _Src_last,  
    Concurrency::accelerator_view _Av,  
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

 
template <
    typename _InputIterator  
>  
array(
    int _E0, _InputIterator _Src_first,  
    Concurrency::accelerator_view _Av,  
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

 
template <
    typename _InputIterator  
>  
array(
    int _E0,  
    int _E1, _InputIterator _Src_first, _InputIterator _Src_last,  
    Concurrency::accelerator_view _Av,  
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

 
template <
    typename _InputIterator  
>  
array(
    int _E0,  
    int _E1, _InputIterator _Src_first,  
    Concurrency::accelerator_view _Av,  
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

 
template <
    typename _InputIterator  
>  
array(
    int _E0,  
    int _E1,  
    int _E2, _InputIterator _Src_first, _InputIterator _Src_last,  
    Concurrency::accelerator_view _Av,  
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

 
template <
    typename _InputIterator  
>  
array(
    int _E0,  
    int _E1,  
    int _E2, _InputIterator _Src_first,  
    Concurrency::accelerator_view _Av,  
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

 
explicit array(
    const array_view<const value_type, _Rank>& _Src) restrict(cpu);

 
array(
    const array_view<const value_type, _Rank>& _Src,  
    accelerator_view _Av  
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

 
array(
    const array_view<const value_type, _Rank>& _Src,  
    accelerator_view _Av,  
    accelerator_view _Associated_Av) restrict(cpu);

 
array(
    const array& _Other) restrict(cpu);

 
array(
    array&& _Other) restrict(cpu);
```  
  
### <a name="parameters"></a>參數  
 `_Associated_Av`  
 Accelerator_view 指定慣用的目標位置的陣列。  
  
 `_Av`  
  [Accelerator_view](../../../parallel/amp/reference/accelerator-view-class.md) 物件，指定陣列的位置。  
  
 `_Cpu_access_type`  
 想要的 [access_type](access_type%20Enumeration.md)  CPU 上的陣列。 此參數的預設值是 `access_type_auto` 離開 CPU `access_type` 至執行階段決定。 實際 CPU `access_type` 陣列可以使用查詢的 `get_cpu_access_type` 方法。  
  
 `_Extent`  
 陣列的每個維度中的延伸區。  
  
 `_E0`  
 本章節的範圍的最重要的元件。  
  
 `_E1`  
 本章節的範圍的下一步-至-最大顯著性的元件。  
  
 `_E2`  
 本章節的範圍的最小顯著性的元件。  
  
 `_InputIterator`  
 輸入 interator 型別。  
  
 `_Src`  
 若要複製的物件。  
  
 `_Src_first`  
 在來源容器的開頭迭代器。  
  
 `_Src_last`  
 結束迭代器，為來源容器。  
  
 `_Other`  
 其他資料來源。  
  
 `_Rank`  
 區段的陣序規範。  
  
 `value_type`  
 複製的項目資料型別。  
  
##  <a name="a-namearrayassociatedacceleratorviewdatamembera-arrayassociatedacceleratorview-data-member"></a><a name="array__associated_accelerator_view_data_member"></a>  array:: associated_accelerator_view 資料成員  
 取得第二個 [accelerator_view](../../../parallel/amp/reference/accelerator-view-class.md) 臨時的建構函式呼叫來具現化時，做為參數傳遞的物件 [陣列](../../../parallel/amp/reference/array-class.md) 物件。  
  
```  
__declspec(property(get= get_associated_accelerator_view)) Concurrency::accelerator_view associated_accelerator_view;  
```  
  
##  <a name="a-namearraycopytomethoda-arraycopyto-method"></a><a name="array__copy_to_method"></a>  array:: copy_to 方法  
 複製的內容 [陣列](../../../parallel/amp/reference/array-class.md) 到另一個 `array`。  
  
```  
void copy_to(
    array<value_type, _Rank>& _Dest) const ;  
 
void copy_to(
    array_view<value_type, _Rank>& _Dest) const ;  
```  
  
### <a name="parameters"></a>參數  
 `_Dest`  
  [Array_view](../../../parallel/amp/reference/array-view-class.md) 複製到的物件。  
  
##  <a name="a-namearraycpuaccesstypedatamembera-arraycpuaccesstype-data-member"></a><a name="array__cpu_access_type_data_member"></a>  array:: cpu_access_type 資料成員  
 取得這個陣列所允許的 CPU access_type。  
  
```  
__declspec(property(get= get_cpu_access_type)) access_type cpu_access_type;  
```  
  
##  <a name="a-namearraydatamethoda-arraydata-method"></a><a name="array__data_method"></a>  array:: data 方法  
 傳回的未經處理資料的指標 [陣列](../../../parallel/amp/reference/array-class.md)。  
  
```  
value_type* data() restrict(amp,
    cpu);

 
const value_type* data() const restrict(amp,
    cpu);
```  
  
### <a name="return-value"></a>傳回值  
 未經處理資料的陣列指標。  
  
##  <a name="a-namearrayextentdatamembera-arrayextent-data-member"></a><a name="array__extent_data_member"></a>  array:: extent 資料成員  
 取得 [範圍](../../../parallel/amp/reference/extent-class-cpp-amp.md) 定義的圖形物件 [陣列](../../../parallel/amp/reference/array-class.md)。  
  
```  
__declspec(property(get= get_extent)) Concurrency::extent<_Rank> extent;  
```  
  
##  <a name="a-namearraygetacceleratorviewmethoda-arraygetacceleratorview-method"></a><a name="array__get_accelerator_view_method"></a>  array:: get_accelerator_view 方法  
 傳回 [accelerator_view](../../../parallel/amp/reference/accelerator-view-class.md) 物件代表的位置，其中 [陣列](../../../parallel/amp/reference/array-class.md) 物件配置。 這個屬性可以只在 CPU 上存取。  
  
```  
Concurrency::accelerator_view get_accelerator_view() const;

 
```  
  
### <a name="return-value"></a>傳回值  
  `accelerator_view` 物件代表的位置，其中 [陣列](../../../parallel/amp/reference/array-class.md) 物件配置。  
  
##  <a name="a-namearraygetassociatedacceleratorviewmethoda-arraygetassociatedacceleratorview-method"></a><a name="array__get_associated_accelerator_view_method"></a>  array:: get_associated_accelerator_view 方法  
 取得第二個 [accelerator_view](../../../parallel/amp/reference/accelerator-view-class.md) 臨時的建構函式呼叫來具現化時，做為參數傳遞的物件 [陣列](../../../parallel/amp/reference/array-class.md) 物件。  
  
```  
Concurrency::accelerator_view get_associated_accelerator_view() const ;  
```  
  
### <a name="return-value"></a>傳回值  
 第二個 [accelerator_view](../../../parallel/amp/reference/accelerator-view-class.md) 物件傳遞至開發用的建構函式。  
  
##  <a name="a-namearraygetcpuaccesstypemethoda-arraygetcpuaccesstype-method"></a><a name="array__get_cpu_access_type_method"></a>  array:: get_cpu_access_type 方法  
 允許為這個陣列傳回 CPU access_type。  
  
```  
access_type get_cpu_access_type() const restrict(cpu);
```  
  
### <a name="return-value"></a>傳回值  
  
##  <a name="a-namearraygetextentmethoda-arraygetextent-method"></a><a name="array__get_extent_method"></a>  array:: get_extent 方法  
 傳回 [範圍](../../../parallel/amp/reference/extent-class-cpp-amp.md) 物件 [陣列](../../../parallel/amp/reference/array-class.md)。  
  
```  
Concurrency::extent<_Rank> get_extent() const restrict(amp,cpu);
```  
  
### <a name="return-value"></a>傳回值  
  `extent` 物件 [陣列](../../../parallel/amp/reference/array-class.md)。  
  
##  <a name="a-namearrayoperatorstdvectorltvaluetypegtoperatora-arrayoperator-stdvectorltvaluetypegt-operator"></a><a name="array__operator_std__vector_lt__value_type_gt__operator"></a>  array:: operator std:: vector&lt;value_type&gt; 運算子  
 使用 `copy(*this, vector)` 來隱含地轉換成 std:: vector 物件的陣列。  
  
'' 運算子 std:: vector \< value_type > （） const restrict （cpu)。
```  
  
### Parameters  
 `value_type`  
 The data type of the elements of the vector.  
  
### Return Value  
 An object of type `vector<T>` that contains a copy of the data that is contained in the array.  
  
##  <a name="array__operator___operator"></a>  array::operator() Operator  
 Returns the element value that is specified by the parameters.  
  
```  
value_type & operator （) const 索引 \< _Rank > & _Index restrict(amp,cpu);

 
const value_type 和 operator （） (const 索引 \< _Rank > & _Index) const restrict(amp,cpu);

 
value_type & operator （) （int _I0，int _I1） restrict(amp,cpu);

 
const value_type & const restrict(amp,cpu) operator （) （int _I0，int _I1）;

 
value_type & operator （) （int _I0、 int _I1，int _I2） restrict(amp,cpu);

 
const value_type & const restrict(amp,cpu) operator （) （int _I0、 int _I1，int _I2）;

 
typename details::_Projection_result_type \< value_type、 _Rank >:: _Result_type operator （) （int （_i）） restrict(amp,cpu);

 
typename details::_Projection_result_type \< value_type、 _Rank >:: operator （) （int （_i）） const restrict(amp,cpu) _Const_result_type;
```  
  
### Parameters  
 `_Index`  
 The location of the element.  
  
 `_I0`  
 The most significant component of the origin of this section.  
  
 `_I1`  
 The next-to-most-significant component of the origin of this section.  
  
 `_I2`  
 The least significant component of the origin of this section.  
  
 `_I`  
 The location of the element.  
  
### Return Value  
 The element value specified by the parameters.  
  
##  <a name="array__operator_at_operator"></a>  array::operator[] Operator  
 Returns the element that is at the specified index.  
  
```  
value_type & 運算子 [] (const 索引 \< _Rank > & _Index) restrict(amp,cpu);

 
const value_type & 運算子 [] (const 索引 \< _Rank > & _Index) const restrict(amp,cpu);

 
typename details::_Projection_result_type \< value_type、 _Rank >:: _Result_type 運算子[](int _I) restrict(amp,cpu);

 
typename details::_Projection_result_type \< value_type、 _Rank >:: _Const_result_type 運算子[](int _I) const restrict(amp,cpu);
```  
  
### Parameters  
 `_Index`  
 The index.  
  
 `_I`  
 The index.  
  
### Return Value  
 The element that is at the specified index.  
  
##  <a name="array__operator_eq_operator"></a>  array::operator= Operator  
 Copies the contents of the specified [array](../../../parallel/amp/reference/array-class.md) object.  
  
```  
陣列 （&) 運算子 = const 陣列 & _Other restrict （cpu)。

 
陣列 （&) 運算子 = (陣列 （& s) （& s) _Other) restrict （cpu)。

 
陣列 （&) 運算子 = (const array_view \< const value_type、 _Rank > & _Src) restrict （cpu)。
```  
  
### Parameters  
 `_Other`  
 The `array` object to copy from.  
  
 `_Src`  
 The `array` object to copy from.  
  
### Return Value  
 A reference to this `array` object.  
  
##  <a name="array__rank_constant"></a>  array::rank Constant  
 Stores the rank of the [array](../../../parallel/amp/reference/array-class.md).  
  
```  
靜態 const int 陣序規範 = _Rank;  
```  
  
##  <a name="array__section_method"></a>  array::section Method  
 Returns a subsection of the [array](../../../parallel/amp/reference/array-class.md) object that is at the specified origin and, optionally, that has the specified extent.  
  
```  
array_view \< value_type、 _Rank > 一節 (const Concurrency::index \< _Rank > & _Section_origin，  
    const Concurrency::extent \< _Rank > & _Section_extent) restrict(amp,cpu);

 
array_view \< const value_type、 _Rank > 一節 (const Concurrency::index \< _Rank > & _Section_origin，  
    const Concurrency::extent \< _Rank > & _Section_extent) const restrict(amp,cpu);

 
array_view \< value_type、 _Rank > 區段 const Concurrency::extent \< _Rank > & _Ext restrict(amp,cpu);

 
array_view \< const value_type、 _Rank > 一節 (const Concurrency::extent \< _Rank > & _Ext) const restrict(amp,cpu);

 
array_view \< value_type、 _Rank > 區段 const 索引 \< _Rank > & _Idx restrict(amp,cpu);

 
array_view \< const value_type、 _Rank > 區段 const 索引 \< _Rank > & _Idx const restrict(amp,cpu);

 
array_view \< value_type 1 > 一節 (int _I0，  
    int _E0) restrict(amp,cpu);

 
array_view \< const value_type，1 > 一節 (int _I0，  
    const restrict(amp,cpu) int _E0);

 
array_view \< value_type，2 > 一節 (int _I0，  
    int _I1  
    int _E0  
    int _E1) restrict(amp,cpu);

 
array_view \< const value_type，2 > 一節 (int _I0，  
    int _I1  
    int _E0  
    const restrict(amp,cpu) int _E1);

 
array_view \< value_type 3 > 一節 (int _I0，  
    int _I1  
    int _I2  
    int _E0  
    int _E1  
    int _E2) restrict(amp,cpu);

 
array_view \< const value_type，3 > 一節 (int _I0，  
    int _I1  
    int _I2  
    int _E0  
    int _E1  
    const restrict(amp,cpu) int _E2);
```  
  
### Parameters  
 `_E0`  
 The most significant component of the extent of this section.  
  
 `_E1`  
 The next-to-most-significant component of the extent of this section.  
  
 `_E2`  
 The least significant component of the extent of this section.  
  
 `_Ext`  
 The [extent](../../../parallel/amp/reference/extent-class-cpp-amp.md) object that specifies the extent of the section. The origin is 0.  
  
 `_Idx`  
 The [index](../../../parallel/amp/reference/index-class.md) object that specifies the location of the origin. The subsection is the rest of the extent.  
  
 `_I0`  
 The most significant component of the origin of this section.  
  
 `_I1`  
 The next-to-most-significant component of the origin of this section.  
  
 `_I2`  
 The least significant component of the origin of this section.  
  
 `_Rank`  
 The rank of the section.  
  
 `_Section_extent`  
 The [extent](../../../parallel/amp/reference/extent-class-cpp-amp.md) object that specifies the extent of the section.  
  
 `_Section_origin`  
 The [index](../../../parallel/amp/reference/index-class.md) object that specifies the location of the origin.  
  
 `value_type`  
 The data type of the elements that are copied.  
  
### Return Value  
 Returns a subsection of the `array` object that is at the specified origin and, optionally, that has the specified extent. When only the `index` object is specified, the subsection contains all elements in the associated grid that have indexes that are larger than the indexes of the elements in the `index` object.  
  
##  <a name="array__view_as_method"></a>  array::view_as Method  
 Reinterprets this array as an [array_view](../../../parallel/amp/reference/array-view-class.md) of a different rank.  
  
```  
範本 \< int _New_rank  
>  
array_view \< value_type、 _New_rank > view_as const Concurrency::extent \< _New_rank > & _View_extent restrict(amp,cpu);

 
範本 \< int _New_rank  
>  
array_view \< const value_type、 _New_rank > view_as const Concurrency::extent \< _New_rank > & _View_extent const restrict(amp,cpu);
```  
  
### Parameters  
 `_New_rank`  
 The rank of the `extent` object passed as a parameter.  
  
 `_View_extent`  
 The extent that is used to construct the new [array_view](../../../parallel/amp/reference/array-view-class.md) object.  
  
 `value_type`  
 The data type of the elements in both the original [array](../../../parallel/amp/reference/array-class.md) object and the returned `array_view` object.  
  
### Return Value  
 The [array_view](../../../parallel/amp/reference/array-view-class.md) object that is constructed.  
  
## See Also  
 [Concurrency Namespace (C++ AMP)](../../../parallel/amp/reference/concurrency-namespace-cpp-amp.md)
