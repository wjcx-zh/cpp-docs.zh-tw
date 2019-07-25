---
title: time_get_byname 類別
ms.date: 11/04/2016
f1_keywords:
- xloctime/std::time_get_byname
helpviewer_keywords:
- time_get_byname class
ms.assetid: 6e54153e-da40-4bb9-a942-1a6ce57b30c9
ms.openlocfilehash: b466f8a893a14f7a94ee7b9e54b72e43aa6cf6e3
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68460020"
---
# <a name="timegetbyname-class"></a>time_get_byname 類別

衍生的樣板類別描述可做為類型 `time_get`\<CharType, InputIterator> 的地區設定 facet 的物件。

## <a name="syntax"></a>語法

```cpp
template <class Elem, class InputIterator =
    istreambuf_iterator<CharType, char_traits<CharType>>>
class time_get_byname : public time_get<CharType, InputIterator>
{
public:
    explicit time_get_byname(
    const char* _Locname,
    size_t _Refs = 0);

    explicit time_get_byname(
    const string& _Locname,
    size_t _Refs = 0);

protected:
    virtual ~time_get_byname()
};
```

### <a name="parameters"></a>參數

*_Locname*\
具名地區設定。

*_Refs*\
初始參考計數。

## <a name="requirements"></a>需求

其行為取決於已命名的地區設定 *_Locname*。 每個建構函式會以 [time_get](../standard-library/time-get-class.md#time_get)\<CharType, InputIterator>( `_Refs`) 初始化其基底物件。

## <a name="requirements"></a>需求

**標頭︰** \<locale>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
