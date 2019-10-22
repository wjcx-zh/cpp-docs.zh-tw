---
title: gslice_array 類別
ms.date: 11/04/2016
f1_keywords:
- valarray/std::gslice_array
helpviewer_keywords:
- gslice_array class
ms.assetid: ad1b4514-b14a-4baf-a293-d5a8e8674c75
ms.openlocfilehash: 68ce774128395e941ff80580a02c4ee28a74a4e4
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689602"
---
# <a name="gslice_array-class"></a>gslice_array 類別

內部的輔助類別樣板，透過在 valarray 的一般配量所定義的子集陣列之間提供作業，以支援一般配量物件。

## <a name="syntax"></a>語法

```cpp
template <class Type>
class gslice_array : public gsplice {
public:
    typedef Type value_type;
    void operator=(const valarray<Type>& x) const;

    void operator=(const Type& x) const;

    void operator*=(const valarray<Type>& x) const;

    void operator/=(const valarray<Type>& x) const;

    void operator%=(const valarray<Type>& x) const;

    void operator+=(const valarray<Type>& x) const;

    void operator-=(const valarray<Type>& x) const;

    void operator^=(const valarray<Type>& x) const;

    void operator&=(const valarray<Type>& x) const;

    void operator|=(const valarray<Type>& x) const;

    void operator<<=(const valarray<Type>& x) const;

    void operator>>=(const valarray<Type>& x) const;

// The rest is private or implementation defined
}
```

## <a name="remarks"></a>備註

類別會描述一個物件，它會儲存 `va` 類別[valarray](../standard-library/valarray-class.md) **\<Type >** 的物件參考，以及[gslice](../standard-library/gslice-class.md)類別的物件 `gs`，其中描述要從 `valarray<Type>` 物件選取的專案序列。

您只能藉由撰寫格式為[va&#91;gs&#93;](../standard-library/valarray-class.md#op_at)的運算式來建立 `gslice_array<Type>` 物件。 類別 gslice_array 的成員函式的行為就像是針對 `valarray<Type>` 定義的對應函式簽章，但只有所選項目的順序會受到影響。

類別樣板是由特定 valarray 作業間接建立的，無法直接在程式中使用。 配量注標運算子會改用內部輔助類別範本：

`gslice_array`\< **Type**> `valarray`\< **Type**>:: `operator[]` ( **constgslice&** )。

您只能針對 valarray `va` 的配量 `gsl` 的 `va[gsl]`，撰寫表單的運算式來建立 `gslice_array<Type>` 物件。 類別 gslice_array 的成員函式的行為就像是針對 `valarray<Type>` 定義的對應函式簽章，但只有所選項目的順序會受到影響。 gslice_array 所控制的序列是由配量建構函式的三個參數所定義，亦即第一個配量中第一個元素的索引、每個配量中的元素數目，以及每個配量中元素之間的距離。

在以下範例中：

```cpp
const size_t lv[] = {2, 3};
const size_t dv[] = {7, 2};
const valarray<size_t> len(lv, 2), str(dv, 2);

// va[gslice(3, len, str)] selects elements with
//   indices 3, 5, 7, 10, 12, 14
```

索引必須有效，程序才能有效。

## <a name="example"></a>範例

如需如何宣告及使用 slice_array 的範例，請參閱 [gslice::gslice](../standard-library/gslice-class.md#gslice) 的範例。

## <a name="requirements"></a>需求

**標頭：** \<valarray>

**命名空間:** std

## <a name="see-also"></a>請參閱

[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
