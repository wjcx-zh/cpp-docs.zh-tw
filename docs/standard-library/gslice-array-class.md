---
title: gslice_array 類別 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- valarray/std::gslice_array
dev_langs:
- C++
helpviewer_keywords:
- gslice_array class
ms.assetid: ad1b4514-b14a-4baf-a293-d5a8e8674c75
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ff44a91b4916092e319c7acc0520c49aeb9a5fa4
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2018
ms.locfileid: "38953071"
---
# <a name="gslicearray-class"></a>gslice_array 類別

可藉由提供 valarray 之一般切割所定義的子集陣列之間的作業，支援一般切割物件的內部、輔助的範本類別。

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

此類別描述可儲存物件的參考`va`類別的[valarray](../standard-library/valarray-class.md)**\<型別 >**，以及物件`gs`類別的[gslice](../standard-library/gslice-class.md)其中描述要從選取的元素序列`valarray<Type>`物件。

您建構`gslice_array<Type>`物件只能藉由撰寫運算式的形式[va&#91;gs&#93;](../standard-library/valarray-class.md#op_at)。 Gslice_array 類別的成員函式行為接著便會像對應的函式簽章定義`valarray<Type>`，不過只有選取的元素序列會受到影響。

此樣板類別是由某些 valarray 運算間接建立的，無法直接在程式中使用。 配量註標運算子會改用內部輔助範本類別：

`gslice_array`\< **Type**> `valarray`\< **Type**>:: `operator[]` ( **constgslice&**)。

您建構`gslice_array<Type>`物件只能藉由撰寫運算式的形式`va[gsl]`，配量`gsl`valarray 的`va`。 Gslice_array 類別的成員函式行為接著便會像對應的函式簽章定義`valarray<Type>`，不過只有選取的元素序列會受到影響。 gslice_array 所控制的序列是由配量建構函式的三個參數所定義，亦即第一個配量中第一個元素的索引、每個配量中的元素數目，以及每個配量中元素之間的距離。

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

**標頭：**\<valarray>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
