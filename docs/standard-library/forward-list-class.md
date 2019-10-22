---
title: forward_list 類別
ms.date: 11/04/2016
f1_keywords:
- forward_list/std::forward_list
- forward_list/std::forward_list::allocator_type
- forward_list/std::forward_list::const_iterator
- forward_list/std::forward_list::const_pointer
- forward_list/std::forward_list::const_reference
- forward_list/std::forward_list::difference_type
- forward_list/std::forward_list::iterator
- forward_list/std::forward_list::pointer
- forward_list/std::forward_list::reference
- forward_list/std::forward_list::size_type
- forward_list/std::forward_list::value_type
- forward_list/std::forward_list::assign
- forward_list/std::forward_list::before_begin
- forward_list/std::forward_list::begin
- forward_list/std::forward_list::cbefore_begin
- forward_list/std::forward_list::cbegin
- forward_list/std::forward_list::cend
- forward_list/std::forward_list::clear
- forward_list/std::forward_list::emplace_after
- forward_list/std::forward_list::emplace_front
- forward_list/std::forward_list::empty
- forward_list/std::forward_list::end
- forward_list/std::forward_list::erase_after
- forward_list/std::forward_list::front
- forward_list/std::forward_list::get_allocator
- forward_list/std::forward_list::insert_after
- forward_list/std::forward_list::max_size
- forward_list/std::forward_list::merge
- forward_list/std::forward_list::pop_front
- forward_list/std::forward_list::push_front
- forward_list/std::forward_list::remove
- forward_list/std::forward_list::remove_if
- forward_list/std::forward_list::resize
- forward_list/std::forward_list::reverse
- forward_list/std::forward_list::sort
- forward_list/std::forward_list::splice_after
- forward_list/std::forward_list::swap
- forward_list/std::forward_list::unique
helpviewer_keywords:
- std::forward_list
- std::forward_list::allocator_type
- std::forward_list::const_iterator
- std::forward_list::const_pointer
- std::forward_list::const_reference
- std::forward_list::difference_type
- std::forward_list::iterator
- std::forward_list::pointer
- std::forward_list::reference
- std::forward_list::size_type
- std::forward_list::value_type
- std::forward_list::assign
- std::forward_list::before_begin
- std::forward_list::begin
- std::forward_list::cbefore_begin
- std::forward_list::cbegin
- std::forward_list::cend
- std::forward_list::clear
- std::forward_list::emplace_after
- std::forward_list::emplace_front
- std::forward_list::empty
- std::forward_list::end
- std::forward_list::erase_after
- std::forward_list::front
- std::forward_list::get_allocator
- std::forward_list::insert_after
- std::forward_list::max_size
- std::forward_list::merge
- std::forward_list::pop_front
- std::forward_list::push_front
- std::forward_list::remove
- std::forward_list::remove_if
- std::forward_list::resize
- std::forward_list::reverse
- std::forward_list::sort
- std::forward_list::splice_after
- std::forward_list::swap
- std::forward_list::unique
ms.openlocfilehash: f1015e53e137b9001bd90233c281345d474bc03f
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689693"
---
# <a name="forward_list-class"></a>forward_list 類別

描述一個控制不同長度項目序列的物件。 這個序列會儲存為節點的單一連結清單，每個清單都包含一個 `Type` 類型的成員。

## <a name="syntax"></a>語法

```cpp
template <class Type,
    class Allocator = allocator<Type>>
class forward_list
```

### <a name="parameters"></a>參數

類型 * \
要儲存在 forward_list 中的項目資料類型。

配置*器 \*
預存配置器物件，可封裝有關 forward_list 之記憶體配置和解除配置的詳細資料。 這是選擇性參數。 預設值為 allocator<`Type`>。

## <a name="remarks"></a>備註

@No__t_0 物件會透過以配置器[類別](../standard-library/allocator-class.md)（通常稱為 `std::allocator)`）為基礎的預存*物件，配置*並釋放它所控制之序列的儲存體。 如需詳細資訊，請參閱[配置器](../standard-library/allocators.md)。 配置器物件必須與 `allocator` 類型的物件具有相同的外部介面。

> [!NOTE]
> 如果已指派容器物件，就不會複製預存配置器物件。

當透過 `forward_list` 清除受控制序列的項目時，迭代器、指標和參考可能會變成無效。 透過 `forward_list` 在受控制的序列上執行插入和接合不會使迭代器無效。

呼叫 [forward_list::insert_after](#insert_after) (其為呼叫建構函式 `Type(const  T&)` 的唯一成員函式) 時，可能會導致受控制序列產生新增項目。 `forward_list` 也可能會呼叫移動建構函式。 如果這類運算式擲回例外狀況，容器物件不會插入任何新項目，而且會重新擲回例外狀況。 因此，當發生這類例外狀況時，`forward_list` 類型的物件會保留為已知狀態。

## <a name="members"></a>Members

### <a name="constructors"></a>建構函式

|||
|-|-|
|[forward_list](#forward_list)|建構類型 `forward_list` 的物件。|

### <a name="typedefs"></a>Typedef

|||
|-|-|
|[allocator_type](#allocator_type)|此類型代表轉送清單物件的配置器類別。|
|[const_iterator](#const_iterator)|此類型提供轉送清單的常數迭代器。|
|[const_pointer](#const_pointer)|一種類型，提供轉送清單中**const**元素的指標。|
|[const_reference](#const_reference)|此類型提供轉送清單中項目的常數參考。|
|[difference_type](#difference_type)|帶正負號的整數類型，可用來代表迭代器所指向的項目間之範圍中的轉送清單項目數。|
|[iterator](#iterator)|提供轉送清單之迭代器的類型。|
|[pointer](#pointer)|此類型提供轉送清單中的項目指標。|
|[reference](#reference)|此類型提供轉送清單中的項目參考。|
|[size_type](#size_type)|此類型代表兩個項目間不帶正負號的間距。|
|[value_type](#value_type)|此類型代表儲存在轉送清單中的項目類型。|

### <a name="functions"></a>函式

|||
|-|-|
|[assign](#assign)|從轉送清單中清除項目，並將一組新的項目複製到目標轉送清單。|
|[before_begin](#before_begin)|傳回迭代器，其定址轉送清單中第一個項目之前的位置。|
|[begin](#begin)|傳回迭代器，其定址轉送清單中的第一個項目。|
|[cbefore_begin](#cbefore_begin)|傳回常數迭代器，其定址轉送清單中第一個項目之前的位置。|
|[cbegin](#cbegin)|傳回常數迭代器，其定址轉送清單中的第一個項目。|
|[cend](#cend)|傳回常數迭代器，其定址轉送清單中最後一個項目之後的位置。|
|[clear](#clear)|清除轉送清單的所有項目。|
|[emplace_after](#emplace_after)|在指定位置之後移動建構新項目。|
|[emplace_front](#emplace_front)|將就地建構的項目加入清單的開頭。|
|[empty](#empty)|測試轉送清單是否空白。|
|[end](#end)|傳回迭代器，其定址轉送清單中最後一個項目之後的位置。|
|[erase_after](#erase_after)|從轉送清單中移除指定位置之後的項目。|
|[front](#front)|傳回轉送清單中第一個項目的參考。|
|[get_allocator](#get_allocator)|傳回用來建構轉送清單的配置器物件複本。|
|[insert_after](#insert_after)|將項目加入轉送清單中的指定位置之後。|
|[max_size](#max_size)|傳回轉送清單的最大長度。|
|[merge](#merge)|從引數清單中移除項目，並將其插入目標轉送清單中，然後以遞增順序或其他指定的順序，排序新合併的項目集合。|
|[pop_front](#pop_front)|刪除轉送清單開頭的項目。|
|[push_front](#push_front)|將項目加入轉送清單的開頭。|
|[remove](#remove)|清除轉送清單中符合指定值的項目。|
|[remove_if](#remove_if)|從轉送清單中清除符合指定述詞的項目。|
|[resize](#resize)|指定轉送清單的新大小。|
|[reverse](#reverse)|反轉項目在轉送清單中出現的順序。|
|[sort](#sort)|以遞增順序或述詞指定的順序排列項目。|
|[splice_after](#splice_after)|重新拼接節點之間的連結。|
|[swap](#swap)|交換兩個轉送清單的項目。|
|[unique](#unique)|移除通過指定測試的相鄰項目。|

### <a name="operators"></a>運算子

|||
|-|-|
|[operator=](#op_eq)|以另一個轉送清單複本取代轉送清單的項目。|

## <a name="allocator_type"></a>allocator_type

此類型代表轉送清單物件的配置器類別。

```cpp
typedef Allocator allocator_type;
```

### <a name="remarks"></a>備註

`allocator_type` 與範本參數 Allocator 同義。

## <a name="assign"></a>值賦

從轉送清單中清除項目，並將一組新的項目複製到目標轉送清單。

```cpp
void assign(
    size_type Count,
    const Type& Val);

void assign(
    initializer_list<Type> IList);

template <class InputIterator>
void assign(InputIterator First, InputIterator Last);
```

### <a name="parameters"></a>參數

*第一個*\
取代範圍的開頭。

*上次*\
取代範圍的結尾。

*計數*\
要指派的元素數目。

*val* \
要指派給每個元素的值。

*類型*\
值的類型。

*IList* \
要複製的 initializer_list。

### <a name="remarks"></a>備註

如果 forward_lis 是整數類型，第一個成員函式的行為即與 `assign((size_type)First, (Type)Last)` 相同。 否則，第一個成員函式會將 `*this` 所控制的序列取代為 [ `First, Last)` 序列，其不得與初始的受控制序列重疊。

第二個成員函式會將 `*this` 所控制的序列，取代為 `Val` 值的 `Count` 個元素數重複。

第三個成員函式會將 initializer_list 的元素複製到 forward_list。

## <a name="before_begin"></a>before_begin

傳回迭代器，其定址轉送清單中第一個項目之前的位置。

```cpp
const_iterator before_begin() const;
iterator before_begin();
```

### <a name="return-value"></a>傳回值

正向迭代器，指向序列的第一個元素正前方 (或空序列結尾正前方的位置)。

### <a name="remarks"></a>備註

## <a name="begin"></a>起點

傳回迭代器，其定址轉送清單中的第一個項目。

```cpp
const_iterator begin() const;
iterator begin();
```

### <a name="return-value"></a>傳回值

傳回正向迭代器，指向序列的第一個元素 (或空序列結尾以外的位置)。

### <a name="remarks"></a>備註

## <a name="cbefore_begin"></a>cbefore_begin

傳回常數迭代器，其定址轉送清單中第一個項目之前的位置。

```cpp
const_iterator cbefore_begin() const;
```

### <a name="return-value"></a>傳回值

正向迭代器，指向序列的第一個元素正前方 (或空序列結尾正前方的位置)。

### <a name="remarks"></a>備註

## <a name="cbegin"></a>cbegin

傳回**常數**反覆運算器，定址範圍中的第一個元素。

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>傳回值

**常數**正向存取反覆運算器，指向範圍的第一個專案，或指向空白範圍結尾之外的位置（針對空白範圍，`cbegin() == cend()`）。

### <a name="remarks"></a>備註

傳回值為 `cbegin` 時，無法修改範圍中的項目。

您可以使用此成員函式取代 `begin()` 成員函式，以確保傳回值是 `const_iterator`。 通常，它是與 [auto](../cpp/auto-cpp.md) 類型推算關鍵字一起使用，如下列範例所示。 在此範例中，請將 `Container` 視為支援 `begin()` 和 `cbegin()` 之任何種類的可修改（非**const**）容器。

```cpp
auto i1 = Container.begin();
// i1 is Container<T>::iterator
auto i2 = Container.cbegin();
// i2 is Container<T>::const_iterator
```

## <a name="cend"></a>cend

傳回**常數**反覆運算器，定址範圍中最後一個元素之後的位置。

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>傳回值

指向範圍結尾之外的正向存取迭代器。

### <a name="remarks"></a>備註

`cend` 用來測試迭代器是否已超過其範圍結尾。

您可以使用此成員函式取代 `end()` 成員函式，以確保傳回值是 `const_iterator`。 通常，它是與 [auto](../cpp/auto-cpp.md) 類型推算關鍵字一起使用，如下列範例所示。 在此範例中，請將 `Container` 視為支援 `end()` 和 `cend()` 之任何種類的可修改（非**const**）容器。

```cpp
auto i1 = Container.end();
// i1 is Container<T>::iterator
auto i2 = Container.cend();

// i2 is Container<T>::const_iterator
```

`cend` 所傳回的值不應該取值。

## <a name="clear"></a>明確

清除轉送清單的所有項目。

```cpp
void clear();
```

### <a name="remarks"></a>備註

此成員函式會呼叫 `erase_after(before_begin(), end()).`。

## <a name="const_iterator"></a>const_iterator

此類型提供轉送清單的常數迭代器。

```cpp
typedef implementation-defined const_iterator;
```

### <a name="remarks"></a>備註

`const_iterator` 描述的物件可作為受控制序列的常數正向迭代器。 在此將其描述為與實作定義的類型同義。

## <a name="const_pointer"></a>const_pointer

一種類型，提供轉送清單中**const**元素的指標。

```cpp
typedef typename Allocator::const_pointer
    const_pointer;
```

### <a name="remarks"></a>備註

## <a name="const_reference"></a>const_reference

此類型提供轉送清單中項目的常數參考。

```cpp
typedef typename Allocator::const_reference const_reference;
```

### <a name="remarks"></a>備註

## <a name="difference_type"></a>difference_type

帶正負號的整數類型，可用來代表迭代器所指向的項目間之範圍中的轉送清單項目數。

```cpp
typedef typename Allocator::difference_type difference_type;
```

### <a name="remarks"></a>備註

`difference_type` 描述的物件可代表受控制序列中任兩個元素位址之間的差距。

## <a name="emplace_after"></a>emplace_after

在指定位置之後移動建構新項目。

```cpp
template <class T>
iterator emplace_after(const_iterator Where, Type&& val);
```

### <a name="parameters"></a>參數

*Where* \
目標轉送清單中新元素的建構位置。

*val* \
建構函式引數。

### <a name="return-value"></a>傳回值

指定新插入之元素的迭代器。

### <a name="remarks"></a>備註

此成員函式會在受控制*序列中所指向的元素*後面，插入具有「函數引數」 *val*的元素。 否則，其行為與 [forward_list::insert_after](#insert_after) 相同。

## <a name="emplace_front"></a>emplace_front

將就地建構的項目加入清單的開頭。

```cpp
template <class Type>
    void emplace_front(Type&& val);
```

### <a name="parameters"></a>參數

*val* \
新增至轉送清單開頭的元素。

### <a name="remarks"></a>備註

此成員函式會將具有 `_ val` 建構函式引數的元素，插入受控制序列的結尾。

如果擲回例外狀況，容器會保持不變，並重新擲回例外狀況。

## <a name="empty"></a>空

測試轉送清單是否空白。

```cpp
bool empty() const;
```

### <a name="return-value"></a>傳回值

如果轉送清單是空的，則為**true** ;否則**為 false**。

## <a name="end"></a>成品

傳回迭代器，其定址轉送清單中最後一個項目之後的位置。

```cpp
const_iterator end() const;
iterator end();
```

### <a name="return-value"></a>傳回值

指向序列結尾之外的正向迭代器。

## <a name="erase_after"></a>erase_after

從轉送清單中移除指定位置之後的項目。

```cpp
iterator erase_after(const_iterator Where);
iterator erase_after(const_iterator first, const_iterator last);
```

### <a name="parameters"></a>參數

*Where* \
目標轉送清單中元素的清除位置。

*第一個*\
要清除的範圍開頭。

*上次*\
要清除的範圍結尾。

### <a name="return-value"></a>傳回值

迭代器，其指定任何移除元素之外的第一個剩餘元素；如果沒有這個元素，則為 [forward_list::end](#end)。

### <a name="remarks"></a>備註

第一個成員函式會在*Where*之後移除受控制序列的元素。

第二個成員函式會移除 `( first,  last)` 範圍中受控制序列中的元素 (不含結束點)。

清除 `N` 元素時，會引發呼叫 `N` 解構函式。 隨即發生[重新配置](../standard-library/forward-list-class.md)，因此已刪除元素的迭代器和參考會變成無效。

成員函式永遠不會擲回例外狀況。

## <a name="forward_list"></a>forward_list

建構類型 `forward_list` 的物件。

```cpp
forward_list();
explicit forward_list(const Allocator& Al);
explicit forward_list(size_type Count);
forward_list(size_type Count, const Type& Val);
forward_list(size_type Count, const Type& Val, const Allocator& Al);
forward_list(const forward_list& Right);
forward_list(const forward_list& Right, const Allocator& Al);
forward_list(forward_list&& Right);
forward_list(forward_list&& Right, const Allocator& Al);
forward_list(initializer_list<Type> IList, const Alloc& Al);
template <class InputIterator>
forward_list(InputIterator First, InputIterator Last);
template <class InputIterator>
forward_list(InputIterator First, InputIterator Last, const Allocator& Al);
```

### <a name="parameters"></a>參數

*Al* \
搭配這個物件使用的配置器類別。

*計數*\
建構的清單中元素的數目。

*Val* \
已建構清單中的元素值。

*Right* \
list，其中有要複製的建構的 list。

*第一個*\
要複製的元素範圍中第一個元素的位置。

*上次*\
超出要複製之元素範圍的第一個元素的位置。

*IList* \
要複製的 initializer_list。

### <a name="remarks"></a>備註

所有建構函式都會儲存[配置器](../standard-library/allocator-class.md)，並初始化受控制的序列。 配置器物件是引數*Al*（如果有的話）。 若是複製建構函式，則為 ` right.get_allocator()`。 否則為 `Allocator()`。

前兩個建構函式指定空的初始受控制序列。

第三個函式會指定值 `Type()` 的*Count*元素重複。

第四個和第五個函式會指定值*Val*的*Count*元素重複。

第六個函式會指定由*右*所控制的序列複本。 如果 `InputIterator` 是整數類型，接下來兩個建構函式會指定 `(Type)Last` 值的 `(size_type)First` 元素重複。 否則，接下來兩個建構函式會指定 `[First, Last)` 序列。

第九個和第十個建構函式與第六個相同，但具有[右值](../cpp/rvalue-reference-declarator-amp-amp.md)參考。

最後一個建構函式會使用 `initializer_list<Type>` 類別的物件，來指定初始的受控制序列。

## <a name="front"></a>前端

傳回轉送清單中第一個項目的參考。

```cpp
reference front();
const_reference front() const;
```

### <a name="return-value"></a>傳回值

受控制序列的第一個元素的參考，且不得為空值。

## <a name="get_allocator"></a>get_allocator

傳回用來建構轉送清單的配置器物件複本。

```cpp
allocator_type get_allocator() const;
```

### <a name="return-value"></a>傳回值

取得預存的[配置器](../standard-library/allocator-class.md)物件。

## <a name="insert_after"></a>insert_after

將項目加入轉送清單中的指定位置之後。

```cpp
iterator insert_after(const_iterator Where, const Type& Val);
void insert_after(const_iterator Where, size_type Count, const Type& Val);
void insert_after(const iterator Where, initializer_list<Type> IList);
iterator insert_after(const_iterator Where, Type&& Val);
template <class InputIterator>
    void insert_after(const_iterator Where, InputIterator First, InputIterator Last);
```

### <a name="parameters"></a>參數

*Where* \
目標轉送清單中第一個元素的插入位置。

*計數*\
要插入的元素數目。

*第一個*\
插入範圍的開頭。

*上次*\
插入範圍的結尾。

*Val* \
新增至轉送清單的元素。

*IList* \
要插入的 initializer_list。

### <a name="return-value"></a>傳回值

指定新插入之元素的迭代器 (僅限第一個和最後一個成員函式)。

### <a name="remarks"></a>備註

每個成員函式都會插入，*緊接在受控制序列中所*指向的元素後面，也就是由其餘運算元所指定的序列。

第一個成員函式會插入具有值*Val*的元素，並傳回反覆運算器，指定新插入的專案。

第二個成員函式會插入 value *Val*的*Count*元素的重複專案。

如果 `InputIterator` 是整數類型，第三個成員函式的行為即與 `insert(it, (size_type)First, (Type)Last)` 相同。 否則，它會插入 `[First, Last)` 序列，其不得與初始的受控制序列重疊。

第四個成員函式會插入由 `initializer_list<Type>` 類別的物件所指定的序列。

最後一個成員函式與第一個相同，但其具有[右值](../cpp/rvalue-reference-declarator-amp-amp.md)參考。

插入 `N` 元素時，會引發呼叫 `N` 建構函式。 隨即發生[重新配置](../standard-library/forward-list-class.md)，但沒有任何迭代器或參考會變成無效。

如果在插入一或多個元素時擲回例外狀況，容器就會保持不變，並重新擲回例外狀況。

## <a name="iterator"></a>定位

提供轉送清單之迭代器的類型。

```cpp
typedef implementation-defined iterator;
```

### <a name="remarks"></a>備註

`iterator` 說明可作為受控制序列之正向迭代器的物件。 在此將其描述為與實作定義的類型同義。

## <a name="max_size"></a>max_size

傳回轉送清單的最大長度。

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>傳回值

物件可以控制的最長序列長度。

### <a name="remarks"></a>備註

## <a name="merge"></a>merge

在線性時間中，將兩個已排序的序列結合成單一已排序的序列。 從引數清單中移除元素，並將它們插入這個 `forward_list`。 兩份清單應該先依照相同的比較函式物件進行排序，再呼叫 `merge`。 結合後的清單將會依據上述比較函式物件來進行排序。

```cpp
void merge(forward_list& right);
template <class Predicate>
    void merge(forward_list& right, Predicate comp);
```

### <a name="parameters"></a>參數

*right* \
要合併的來源轉送清單。

*comp* \
比較函式物件，用於排序元素。

### <a name="remarks"></a>備註

`forward_list::merge` 會從 `forward_list` `right` 移除元素，並將它們插入這個 `forward_list`。 如下所述，兩個序列必須由相同的述詞來排序。 結合後的序列也會根據該比較函式物件來排序。

如果迭代器 `Pi` 和`Pj` 有指定 `i` 和 `j` 位置的元素，則每當 `i < j`，第一個成員函式會強加 `!(*Pj < *Pi)` 的順序 （元素會依照 `ascending` 順序排序）。第二個成員函式會在 `i < j` 時，強加 `! comp(*Pj, *Pi)` 順序。

原始受控制序列中的任何成對元素，皆不會在產生的受控制序列中受到反轉。 在產生的控制序列中，如果某對元素比較的結果相等 ( `!(*Pi < *Pj) && !(*Pj < *Pi)`)，則來自原始受控制序列的元素會出現在來自 `right` 所控制之序列的元素之前。

僅有當 `comp` 擲回例外狀況時，才會發生例外狀況。 在此情況下，受控制的序列會處於未指定的順序，並重新擲回例外狀況。

## <a name="op_eq"></a>operator =

以另一個轉送清單複本取代轉送清單的項目。

```cpp
forward_list& operator=(const forward_list& right);
forward_list& operator=(initializer_list<Type> IList);
forward_list& operator=(forward_list&& right);
```

### <a name="parameters"></a>參數

*right* \
要複製到轉送清單中的轉送清單。

*IList* \
以大括號括住的初始設定式清單，其行為就像是 `Type` 類型的元素序列。

### <a name="remarks"></a>備註

第一個成員運算子會將受控制序列取代為*right*所控制之序列的複本。

第二個成員運算子會取代來自 `initializer_list<Type>` 類別物件的受控制序列。

第三個成員運算子與第一個相同，但其具有[右值](../cpp/rvalue-reference-declarator-amp-amp.md)參考。

## <a name="pointer"></a>滑鼠

此類型提供轉送清單中的項目指標。

```cpp
typedef typename Allocator::pointer pointer;
```

## <a name="pop_front"></a>pop_front

刪除轉送清單開頭的項目。

```cpp
void pop_front();
```

### <a name="remarks"></a>備註

正向清單的第一個元素不得為空值。

成員函式永遠不會擲回例外狀況。

## <a name="push_front"></a>push_front

將項目加入轉送清單的開頭。

```cpp
void push_front(const Type& val);
void push_front(Type&& val);
```

### <a name="parameters"></a>參數

*val* \
新增至轉送清單開頭的元素。

### <a name="remarks"></a>備註

如果擲回例外狀況，容器會保持不變，並重新擲回例外狀況。

## <a name="reference"></a>證明

此類型提供轉送清單中的項目參考。

```cpp
typedef typename Allocator::reference reference;
```

## <a name="remove"></a>取消

清除轉送清單中符合指定值的項目。

```cpp
void remove(const Type& val);
```

### <a name="parameters"></a>參數

*val* \
值，由項目持有時，會導致項目從清單移除。

### <a name="remarks"></a>備註

成員函式會從受控制序列中移除迭代器 `P` 指定的所有元素，對其來說 `*P ==  val`。

成員函式永遠不會擲回例外狀況。

## <a name="remove_if"></a>remove_if

從轉送清單中清除符合指定述詞的項目。

```cpp
template <class Predicate>
    void remove_if(Predicate pred);
```

### <a name="parameters"></a>參數

*pred* \
一元述詞，如果元素符合此述詞，就會從清單中刪除該元素。

### <a name="remarks"></a>備註

成員函式會從受控制序列中移除迭代器 `P` 指定的所有元素，對其來說 ` pred(*P)` 為 true。

只有在*pred*擲回例外狀況時，才會發生例外狀況。 在此情況下，受控制的序列會處於未指定的狀態，並重新擲回例外狀況。

## <a name="resize"></a>調整

指定轉送清單的新大小。

```cpp
void resize(size_type _Newsize);
void resize(size_type _Newsize, const Type& val);
```

### <a name="parameters"></a>參數

*_Newsize* \
重新調整過大小之轉送清單中的元素數。

*val* \
要用於填補的值。

### <a name="remarks"></a>備註

成員函式可確保清單因而需要中的元素數目是 *_Newsize*。 如果它必須讓受控制的序列變長，第一個成員函式會附加具有值 `Type()` 的元素，而第二個成員函式會附加具有值*val*的元素。 若要讓受控制序列更短，這兩個成員函式都會有效呼叫 `erase_after(begin() + _Newsize - 1, end())`。

## <a name="reverse"></a>反向

反轉項目在轉送清單中出現的順序。

```cpp
void reverse();
```

## <a name="size_type"></a>size_type

此類型代表兩個項目間不帶正負號的間距。

```cpp
typedef typename Allocator::size_type size_type;
```

### <a name="remarks"></a>備註

此不帶正負號的整數類型所描述的物件可代表任何受控制序列的長度。

## <a name="sort"></a>方式

以遞增順序或述詞指定的順序排列項目。

```cpp
void sort();
template <class Predicate>
void sort(Predicate pred);
```

### <a name="parameters"></a>參數

*pred* \
排序的述詞。

### <a name="remarks"></a>備註

這兩個成員函式都會按照述詞來排序受控制序列中的元素，如下所述。

如果迭代器 `Pi` 和`Pj` 有指定 `i` 和 `j` 位置的元素，則每當 `i < j`，第一個成員函式會強加 `!(*Pj < *Pi)` 的順序 （元素會依照 `ascending` 順序排序）。成員範本函式會在每次 `i < j` 時，強加 `! pred(*Pj, *Pi)` 順序。 原始受控制序列中的任何排序元素，皆不會在產生的受控制序列中受到反轉 (亦即排序是穩定的)。

只有在*pred*擲回例外狀況時，才會發生例外狀況。 在此情況下，受控制的序列會處於未指定的順序，並重新擲回例外狀況。

## <a name="splice_after"></a>splice_after

從來源 forward_list 中移除元素，並將它們插入至目的地 forward_list。

```cpp
// insert the entire source forward_list
void splice_after(const_iterator Where, forward_list& Source);
void splice_after(const_iterator Where, forward_list&& Source);

// insert one element of the source forward_list
void splice_after(const_iterator Where, forward_list& Source, const_iterator Iter);
void splice_after(const_iterator Where, forward_list&& Source, const_iterator Iter);

// insert a range of elements from the source forward_list
void splice_after(
    const_iterator Where,
    forward_list& Source,
    const_iterator First,
    const_iterator Last);

void splice_after(
    const_iterator Where,
    forward_list&& Source,
    const_iterator First,
    const_iterator Last);
```

### <a name="parameters"></a>參數

*Where* \
目的地 forward_list 中的位置，要在其後面插入。

*Source*\
要插入至目的地 forward_list 的來源 forward_list。

*Iter* \
要從來源 forward_list 插入的元素。

*第一個*\
要從來源 forward_list 插入的範圍中的第一個元素。

*上次*\
要從來源 forward_list 插入的範圍外的第一個位置。

### <a name="remarks"></a>備註

第一對成員函式會將由*Source*所控制的序列，插入至*Where*所指向之受控制序列中的元素之後。 它也會從*來源*移除所有元素。 （`&Source` 不能等於**此**）。

第二對成員函式會在*來源*所控制的序列中*Iter*專案之後，將該元素移除，並將它插入至*Where*所指向之受控制序列中的元素之後。 (若 `Where == Iter || Where == ++Iter`，則不會產生任何變更)。

第三對成員函式（範圍接合）會將 `(First, Last)` 所指定的子範圍，從由*來源*控制的序列*中，緊接*在所指向之受控制序列中的元素之後。 它也會從*來源*所控制的序列中移除原始的子範圍。 （如果 `&Source == this`，`(First, Last)` 範圍不能包含在*其中*所指向的元素）。

如果範圍接合插入 `N` 個元素，而且 `&Source != this`，則會將 [iterator](#iterator) 類別的物件遞增 `N` 次。

指定接合元素的迭代器、指標或參考不會變成無效。

### <a name="example"></a>範例

```cpp
// forward_list_splice_after.cpp
// compile with: /EHsc /W4
#include <forward_list>
#include <iostream>

using namespace std;

template <typename S> void print(const S& s) {
    for (const auto& p : s) {
        cout << "(" << p << ") ";
    }

    cout << endl;
}

int main()
{
    forward_list<int> c1{ 10, 11 };
    forward_list<int> c2{ 20, 21, 22 };
    forward_list<int> c3{ 30, 31 };
    forward_list<int> c4{ 40, 41, 42, 43 };

    forward_list<int>::iterator where_iter;
    forward_list<int>::iterator first_iter;
    forward_list<int>::iterator last_iter;

    cout << "Beginning state of lists:" << endl;
    cout << "c1 = ";
    print(c1);
    cout << "c2 = ";
    print(c2);
    cout << "c3 = ";
    print(c3);
    cout << "c4 = ";
    print(c4);

    where_iter = c2.begin();
    ++where_iter; // start at second element
    c2.splice_after(where_iter, c1);
    cout << "After splicing c1 into c2:" << endl;
    cout << "c1 = ";
    print(c1);
    cout << "c2 = ";
    print(c2);

    first_iter = c3.begin();
    c2.splice_after(where_iter, c3, first_iter);
    cout << "After splicing the first element of c3 into c2:" << endl;
    cout << "c3 = ";
    print(c3);
    cout << "c2 = ";
    print(c2);

    first_iter = c4.begin();
    last_iter = c4.end();
    // set up to get the middle elements
    ++first_iter;
    c2.splice_after(where_iter, c4, first_iter, last_iter);
    cout << "After splicing a range of c4 into c2:" << endl;
    cout << "c4 = ";
    print(c4);
    cout << "c2 = ";
    print(c2);
}
```

```Output
Beginning state of lists:c1 = (10) (11)c2 = (20) (21) (22)c3 = (30) (31)c4 = (40) (41) (42) (43)After splicing c1 into c2:c1 =c2 = (20) (21) (10) (11) (22)After splicing the first element of c3 into c2:c3 = (30)c2 = (20) (21) (31) (10) (11) (22)After splicing a range of c4 into c2:c4 = (40) (41)c2 = (20) (21) (42) (43) (31) (10) (11) (22)
```

## <a name="swap"></a>調換

交換兩個轉送清單的項目。

```cpp
void swap(forward_list& right);
```

### <a name="parameters"></a>參數

*right* \
轉送清單，提供要交換的元素。

### <a name="remarks"></a>備註

成員函式會在 `*this` 和*右方*之間交換受控制的序列。 如果 `get_allocator() ==  right.get_allocator()`，它會在固定時間執行上述作業、不擲回例外狀況，亦不會導致任何參考、指標或迭代器 (其指定這兩個受控制序列中的元素) 失效。 否則，它會執行多個元素指派，和與兩個受控制序列中元素數目成正比的建構函式呼叫。

## <a name="unique"></a>唯一

排除所有項目，除了每組連續相等元素的第一個元素以外。

```cpp
void unique();
template <class BinaryPredicate>
void unique(BinaryPredicate comp);
```

### <a name="parameters"></a>參數

*comp* \
供二元述詞用來比較連續元素。

### <a name="remarks"></a>備註

每個唯一元素中的第一個會保留，其餘則移除。 您必須排序元素，以讓相等值的元素在清單中彼此相鄰。

如果任何元素與其前一個元素相等，第一個成員函式會從受控制序列中將其移除。 如果迭代器 `Pi` 和`Pj` 有指定 `i` 和 `j` 位置的元素，則第二個成員函式會移除 `i + 1 == j &&  comp(*Pi, *Pj)` 的每個元素。

如果受控制序列的長度 `N` (> 0)，則 ` comp(*Pi, *Pj)` 述詞會受到 `N - 1` 次評估。

僅有當 `comp` 擲回例外狀況時，才會發生例外狀況。 在此情況下，受控制的序列會處於未指定的狀態，並重新擲回例外狀況。

## <a name="value_type"></a>value_type

此類型代表儲存在轉送清單中的項目類型。

```cpp
typedef typename Allocator::value_type value_type;
```

### <a name="remarks"></a>備註

此類型與範本參數 _ `Ty` 同義。
