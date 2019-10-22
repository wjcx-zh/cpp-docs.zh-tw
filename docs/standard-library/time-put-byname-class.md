---
title: time_put_byname 類別
ms.date: 11/04/2016
f1_keywords:
- xloctime/std::time_put_byname
helpviewer_keywords:
- time_put_byname class
ms.assetid: e08c2348-64d2-4ace-98b1-1496e14c7b1a
ms.openlocfilehash: 4471c0df352a4d40d863ac36f0245cf8194f588c
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/21/2019
ms.locfileid: "72685459"
---
# <a name="time_put_byname-class"></a>time_put_byname 類別

衍生類別範本描述的物件可以做為類型的地區設定 facet，`time_put` \< CharType，OutputIterator >。

## <a name="syntax"></a>語法

```cpp
template <class CharType, class OutIt = ostreambuf_iterator<CharType, char_traits<CharType>>>
class time_put_byname : public time_put<CharType, OutputIterator>
{
public:
    explicit time_put_byname(
    const char* _Locname,
    size_t _Refs = 0);

    explicit time_put_byname(
    const string& _Locname,
    size_t _Refs = 0);

protected:
    virtual ~time_put_byname();

};
```

### <a name="parameters"></a>參數

*_Locname* \
地區設定名稱。

*_Refs* \
初始參考計數。

## <a name="remarks"></a>備註

其行為取決於[已命名](../standard-library/locale-class.md#name)的地區設定 *_Locname*。 每個函式都會使用[time_put](../standard-library/time-put-class.md#time_put) \<CharType、OutputIterator > （`_Refs`）來初始化其基底物件。

## <a name="requirements"></a>需求

**標頭︰** \<locale>

**命名空間:** std

## <a name="see-also"></a>請參閱

[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
