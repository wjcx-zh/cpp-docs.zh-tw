---
title: messages_byname 類別
ms.date: 11/04/2016
f1_keywords:
- xlocmes/std::messages_byname
helpviewer_keywords:
- messages_byname class
ms.assetid: c6c64841-3e80-43c8-b54c-fed41833ad6b
ms.openlocfilehash: 56d8931cb404d9c0f3f5113f8b2ca0f1158209f2
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689335"
---
# <a name="messages_byname-class"></a>messages_byname 類別

衍生類別範本描述可以做為給定地區設定之訊息 facet 的物件，以啟用當地語系化訊息的抓取。

## <a name="syntax"></a>語法

```cpp
template <class CharType>
class messages_byname : public messages<CharType> {
public:
    explicit messages_byname(
    const char *_Locname,
    size_t _Refs = 0);

    explicit messages_byname(
    const string& _Locname,
    size_t _Refs = 0);

protected:
    virtual ~messages_byname();

};
```

### <a name="parameters"></a>參數

*_Locname* \
具名地區設定。

*_Refs* \
初始參考計數。

## <a name="remarks"></a>備註

其行為取決於已命名的地區設定 *_Locname*。 每個建構函式都會以 [messages](../standard-library/messages-class.md#messages)\<CharType>( `_Refs`) 將其基底物件初始化。

## <a name="requirements"></a>需求

**標頭︰** \<locale>

**命名空間:** std

## <a name="see-also"></a>請參閱

[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
