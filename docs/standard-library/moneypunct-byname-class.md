---
title: moneypunct_byname 類別
ms.date: 11/04/2016
f1_keywords:
- xlocmon/std::moneypunct_byname
helpviewer_keywords:
- moneypunct_byname class
ms.assetid: e8a544d2-6aee-420d-b513-deb385c9b416
ms.openlocfilehash: 003ba2136e779c444c7edad9b1759a861a8b0803
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50574430"
---
# <a name="moneypunctbyname-class"></a>moneypunct_byname 類別

衍生的範本類別，描述可作為特定地區設定 `moneypunct` facet 的物件，可用來將貨幣輸入欄位或貨幣輸出欄位格式化。

## <a name="syntax"></a>語法

```cpp
template <class CharType, bool Intl = false>
class moneypunct_byname : public moneypunct<CharType, Intl>
{
public:
    explicit moneypunct_byname(
    const char* _Locname,
    size_t _Refs = 0);

    explicit moneypunct_byname(
    const string& _Locname,
    size_t _Refs = 0);

protected:
    virtual ~moneypunct_byname();

};
```

## <a name="remarks"></a>備註

其行為取決於具名地區設定 `_Locname`。 每個建構函式都會以 [moneypunct](../standard-library/moneypunct-class.md#moneypunct)\<CharType, Intl>( `_Refs`) 將其基底物件初始化。

## <a name="requirements"></a>需求

**標頭︰**\<locale>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
