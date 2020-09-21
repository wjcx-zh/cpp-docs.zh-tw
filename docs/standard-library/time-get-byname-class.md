---
title: time_get_byname 類別
ms.date: 11/04/2016
f1_keywords:
- xloctime/std::time_get_byname
helpviewer_keywords:
- time_get_byname class
ms.assetid: 6e54153e-da40-4bb9-a942-1a6ce57b30c9
ms.openlocfilehash: 040d140fa4250ad33e20d1c2724b6f563e865e6b
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2020
ms.locfileid: "90742654"
---
# <a name="time_get_byname-class"></a>time_get_byname 類別

衍生類別樣板描述可做為型別之地區設定 facet 的物件 `time_get` \<CharType, InputIterator> 。

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

## <a name="requirements"></a>規格需求

其行為取決於命名地區設定 *_Locname*。 每個函式都會使用[time_get](../standard-library/time-get-class.md#time_get) \<CharType, InputIterator> () 來初始化其基底物件 `_Refs` 。

**標頭：**\<locale>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[C + + 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
