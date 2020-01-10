---
title: collate_byname 類別
ms.date: 11/04/2016
f1_keywords:
- locale/std::collate_byname
helpviewer_keywords:
- collate_byname class
ms.assetid: 3dc380df-867c-4763-b60e-ba62a8e63ca7
ms.openlocfilehash: 3e9a256ac7bdb5f6d077746fe2a08990ed41e931
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688276"
---
# <a name="collate_byname-class"></a>collate_byname 類別

衍生類別範本，描述可以做為指定地區設定之 collate facet 的物件，可讓您抓取關於字串排序慣例的文化特性區域特定資訊。

## <a name="syntax"></a>語法

```cpp
template <class CharType>
class collate_byname : public collate<CharType> {
public:
    explicit collate_byname(
    const char* _Locname,
    size_t _Refs = 0);

    explicit collate_byname(
    const string& _Locname,
    size_t _Refs = 0);

protected:
    virtual ~collate_byname();

};
```

### <a name="parameters"></a>參數

*_Locname* \
具名地區設定。

*_Refs* \
初始參考計數。

## <a name="remarks"></a>備註

類別樣板描述的物件可以做為 \<CharType > 之[collate](../standard-library/collate-class.md#collate)類型的[地區設定 facet](../standard-library/locale-class.md#facet_class) 。 其行為取決於[已命名](../standard-library/locale-class.md#name)的地區設定 *_Locname*。 每個建構函式會以 [collate](../standard-library/collate-class.md#collate)\<CharType>( `_Refs`) 初始化其基底物件。

## <a name="requirements"></a>需求

**標頭︰** \<locale>

**命名空間:** std

## <a name="see-also"></a>請參閱

[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
