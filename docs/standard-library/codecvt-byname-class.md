---
title: codecvt_byname 類別 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- xlocale/std::codecvt_byname
dev_langs:
- C++
helpviewer_keywords:
- codecvt_byname class
ms.assetid: b63b6c04-f60c-47b9-8e30-a933f24a8ffb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a785c7868f3a1f3262283cf131bbd3cc3ae88e4c
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2018
ms.locfileid: "44102152"
---
# <a name="codecvtbyname-class"></a>codecvt_byname 類別

衍生的樣板類別，描述可以做為特定地區設定的定序 facet 的物件，啟用有關轉換的文化特性區域特定資訊的擷取。

## <a name="syntax"></a>語法

```cpp
template <class CharType, class Byte, class StateType>
class codecvt_byname: public codecvt<CharType, Byte, StateType> {
public:
    explicit codecvt_byname(
    const char* _Locname,
    size_t _Refs = 0);
```

```cpp
explicit codecvt_byname(
    const string& _Locname,
    size_t _Refs = 0);
```

```cpp
protected:
    virtual ~codecvt_byname();

};
```

### <a name="parameters"></a>參數

*_Locname*<br/>
具名地區設定。

*_Refs*<br/>
初始參考計數。

## <a name="remarks"></a>備註

建構具名地區設定時，會自動建立 Byname Facet。

其行為取決於具名地區設定 *_Locname*。 每個建構函式會以 [codecvt](../standard-library/codecvt-class.md)\<CharType, Byte, StateType>( `_Refs`) 初始化其基底物件。

## <a name="requirements"></a>需求

**標頭︰**\<locale>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
