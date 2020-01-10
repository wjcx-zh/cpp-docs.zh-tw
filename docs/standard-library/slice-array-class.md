---
title: slice_array 類別
ms.date: 11/04/2016
f1_keywords:
- valarray/std::slice_array
helpviewer_keywords:
- slice_array class
ms.assetid: a182d5f7-f35c-4e76-86f2-b5ac64ddc846
ms.openlocfilehash: 358348a57b823fcea82cd296967c83778819361d
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688954"
---
# <a name="slice_array-class"></a>slice_array 類別

內部的輔助類別樣板，藉由在 valarray 的配量所定義的子集陣列之間提供作業，以支援配量物件。

## <a name="syntax"></a>語法

```cpp
template <class Type>
class slice_array : public slice {
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

此類別描述一個物件，該物件會將對 [valarray](../standard-library/valarray-class.md) **\<Type>** 類別之物件的參考與 [slice](../standard-library/slice-class.md) 類別的物件儲存在一起，後者描述要從 **valarray\<Type>** 物件選取的項目序列。

類別樣板是由特定 valarray 作業間接建立的，無法直接在程式中使用。 配量注標運算子所使用的內部、輔助類別範本：

`slice_array`\< **Type**> `valarray`< **Type**:: `operator[]` ( `slice`)。

針對 valarray `va` 的配量 `sl`，您只需要撰寫一個[格式&#91;為&#93;va sl](../standard-library/valarray-class.md#op_at)的運算式，即可建立 `slice_array<Type>` 物件。 類別 slice_array 的成員函式的行為就像是針對 `valarray<Type>` 定義的對應函式簽章，但只有所選項目的順序會受到影響。 slice_array 所控制的序列是由配量建構函式的三個參數所定義，亦即配量中第一個項目的索引、項目數，以及項目之間的距離。 **Va**[`slice` （2，5，3）] 所宣告的 slice_array 從 `va` valarray 剪下，會從 `va` 選取具有索引2、5、8、11和14的元素。 索引必須有效，程序才能有效。

## <a name="example"></a>範例

如需如何宣告及使用 slice_array 的範例，請參閱 [slice::slice](../standard-library/slice-class.md#slice) 的範例。

## <a name="requirements"></a>需求

**標頭：** \<valarray>

**命名空間:** std

## <a name="see-also"></a>請參閱

[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
