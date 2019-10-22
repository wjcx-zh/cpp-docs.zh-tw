---
title: moneypunct_byname 類別
ms.date: 11/04/2016
f1_keywords:
- xlocmon/std::moneypunct_byname
helpviewer_keywords:
- moneypunct_byname class
ms.assetid: e8a544d2-6aee-420d-b513-deb385c9b416
ms.openlocfilehash: c687bc870e4d78cfe9174eb04ea09c34d6a9c955
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/21/2019
ms.locfileid: "72687661"
---
# <a name="moneypunct_byname-class"></a>moneypunct_byname 類別

衍生類別範本，描述可做為給定地區設定之 `moneypunct` facet 的物件，啟用 [貨幣輸入欄位] 或 [貨幣輸出] 欄位的格式。

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

**標頭︰** \<locale>

**命名空間:** std

## <a name="see-also"></a>請參閱

[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
