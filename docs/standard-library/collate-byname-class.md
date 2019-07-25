---
title: collate_byname 類別
ms.date: 11/04/2016
f1_keywords:
- locale/std::collate_byname
helpviewer_keywords:
- collate_byname class
ms.assetid: 3dc380df-867c-4763-b60e-ba62a8e63ca7
ms.openlocfilehash: b8ed428da05e706796a981b8ca9d601033156c6f
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68458615"
---
# <a name="collatebyname-class"></a>collate_byname 類別

衍生的樣板類別，描述可以做為特定地區設定的定序 facet 的物件，啟用有關字串排序慣例的文化特性區域特定資訊的擷取。

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

*_Locname*\
具名地區設定。

*_Refs*\
初始參考計數。

## <a name="remarks"></a>備註

範本類別描述的物件，可作為 [collate](../standard-library/collate-class.md#collate)\<CharType> 類型的[地區設定 Facet](../standard-library/locale-class.md#facet_class)。 其行為取決於[已命名](../standard-library/locale-class.md#name)的地區設定 *_Locname*。 每個建構函式會以 [collate](../standard-library/collate-class.md#collate)\<CharType>( `_Refs`) 初始化其基底物件。

## <a name="requirements"></a>需求

**標頭︰** \<locale>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
