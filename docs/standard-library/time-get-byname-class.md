---
title: time_get_byname 類別
ms.date: 11/04/2016
f1_keywords:
- xloctime/std::time_get_byname
helpviewer_keywords:
- time_get_byname class
ms.assetid: 6e54153e-da40-4bb9-a942-1a6ce57b30c9
ms.openlocfilehash: 9df3831e085f1dea1df45ff9368479fa516b944e
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/21/2019
ms.locfileid: "72685762"
---
# <a name="time_get_byname-class"></a>time_get_byname 類別

衍生類別範本描述的物件可以做為類型的地區設定 facet，`time_get` \<CharType，InputIterator >。

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

*_Locname* \
具名地區設定。

*_Refs* \
初始參考計數。

## <a name="requirements"></a>需求

其行為取決於已命名的地區設定 *_Locname*。 每個建構函式會以 [time_get](../standard-library/time-get-class.md#time_get)\<CharType, InputIterator>( `_Refs`) 初始化其基底物件。

## <a name="requirements"></a>需求

**標頭︰** \<locale>

**命名空間:** std

## <a name="see-also"></a>請參閱

[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
