---
title: time_put_byname 類別 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- xloctime/std::time_put_byname
dev_langs:
- C++
helpviewer_keywords:
- time_put_byname class
ms.assetid: e08c2348-64d2-4ace-98b1-1496e14c7b1a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 62d78fb7c2b9cbaee62baf59636303f90177cf7b
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45699591"
---
# <a name="timeputbyname-class"></a>time_put_byname 類別

衍生的樣板類別描述可做為類型 `time_put`\< CharType, OutputIterator > 的地區設定 facet 的物件。

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

*_Locname*<br/>
地區設定名稱。

*_Refs*<br/>
初始參考計數。

## <a name="remarks"></a>備註

其行為取決於[名為](../standard-library/locale-class.md#name)地區設定 *_Locname*。 每個建構函式會初始化其基底物件[time_put](../standard-library/time-put-class.md#time_put)\<CharType，OutputIterator > (`_Refs`)。

## <a name="requirements"></a>需求

**標頭︰**\<locale>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
