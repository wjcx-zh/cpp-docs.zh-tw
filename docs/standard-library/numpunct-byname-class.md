---
title: numpunct_byname 類別 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- xlocnum/std::numpunct_byname
dev_langs:
- C++
helpviewer_keywords:
- numpunct_byname class
ms.assetid: 18412924-e085-4771-b5e9-7a200cbdd7c0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 511547b8a02a956a2ed7eff2da384f3adcfbd5ed
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
ms.locfileid: "33912793"
---
# <a name="numpunctbyname-class"></a>numpunct_byname 類別

衍生的樣板類別，描述可以做為特定地區設定的 `numpunct` facet 的物件，啟用數值和布林運算式格式和標點符號。

## <a name="syntax"></a>語法

```cpp
template <class CharType>
class numpunct_byname : public numpunct<Elem> {
public:
    explicit numpunct_byname(
    const char* _Locname,
    size_t _Refs = 0);

    explicit numpunct_byname(
    const string& _Locname,
    size_t _Refs = 0);

protected:
    virtual ~numpunct_byname();

};
```

## <a name="remarks"></a>備註

其行為取決於[具名](../standard-library/locale-class.md#name)地區設定 `_Locname`。 建構函式會以 [numpunct](../standard-library/numpunct-class.md#numpunct)\<CharType>( `_Refs`) 初始化其基底物件。

## <a name="requirements"></a>需求

**標頭︰**\<locale>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
