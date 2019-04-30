---
title: slice_array 類別
ms.date: 11/04/2016
f1_keywords:
- valarray/std::slice_array
helpviewer_keywords:
- slice_array class
ms.assetid: a182d5f7-f35c-4e76-86f2-b5ac64ddc846
ms.openlocfilehash: 9577447b2201c1c9e53192b99abad1979f45d15f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62412536"
---
# <a name="slicearray-class"></a>slice_array 類別

可藉由提供 valarray 之切割所定義的子集陣列之間的作業，支援切割物件的內部、輔助的範本類別。

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

此類別描述一個物件，該物件會將對 [valarray](../standard-library/valarray-class.md)**\<Type>** 類別之物件的參考與 [slice](../standard-library/slice-class.md) 類別的物件儲存在一起，後者描述要從 **valarray\<Type>** 物件選取的項目序列。

此樣板類別是由某些 valarray 運算間接建立的，無法直接在程式中使用。 配量註標運算子會使用內部輔助樣板類別：

`slice_array`\< **Type**> `valarray`< **Type**:: `operator[]` ( `slice`)。

您建構`slice_array<Type>`物件只能藉由撰寫運算式的形式[va&#91;sl&#93;](../standard-library/valarray-class.md#op_at)，配量`sl`的 valarray `va`。 Slice_array 類別的成員函式行為接著便會像對應的函式簽章定義`valarray<Type>`，不過只有選取的元素序列會受到影響。 slice_array 所控制的序列是由配量建構函式的三個參數所定義，亦即配量中第一個項目的索引、項目數，以及項目之間的距離。 從 valarray 剪下的 slice_array`va`宣告**va**[ `slice`（2、 5、 3）] 選取項目，以索引 2、 5、 8、 11 和 14 的`va`。 索引必須有效，程序才能有效。

## <a name="example"></a>範例

如需如何宣告及使用 slice_array 的範例，請參閱 [slice::slice](../standard-library/slice-class.md#slice) 的範例。

## <a name="requirements"></a>需求

**標頭：**\<valarray>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
