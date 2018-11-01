---
title: messages_byname 類別
ms.date: 11/04/2016
f1_keywords:
- xlocmes/std::messages_byname
helpviewer_keywords:
- messages_byname class
ms.assetid: c6c64841-3e80-43c8-b54c-fed41833ad6b
ms.openlocfilehash: 7b341f3e1dbf76021911c70560b83932b5302191
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50605313"
---
# <a name="messagesbyname-class"></a>messages_byname 類別

衍生的範本類別，描述可作為特定地區設定訊息 facet 的物件，可用來擷取當地語系化訊息。

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

*_Locname*<br/>
具名地區設定。

*_Refs*<br/>
初始參考計數。

## <a name="remarks"></a>備註

其行為取決於具名地區設定 *_Locname*。 每個建構函式都會以 [messages](../standard-library/messages-class.md#messages)\<CharType>( `_Refs`) 將其基底物件初始化。

## <a name="requirements"></a>需求

**標頭︰**\<locale>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
