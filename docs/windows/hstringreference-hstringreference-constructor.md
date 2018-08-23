---
title: 'Hstringreference:: Hstringreference 建構函式 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::HStringReference
dev_langs:
- C++
ms.assetid: 29f5fe11-3928-4f60-9861-f0894247bfcb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c13635f4b73ee34de11b8c18b0cdd9943b261a29
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42591181"
---
# <a name="hstringreferencehstringreference-constructor"></a>HStringReference::HStringReference 建構函式

初始化的新執行個體**HStringReference**類別。

## <a name="syntax"></a>語法

```cpp
template<unsigned int sizeDest>
HStringReference(wchar_t const (&str)[ sizeDest]) throw();

template<unsigned int sizeDest>
HStringReference(wchar_t const (&str)[ sizeDest],
                 unsigned int len) throw();

HStringReference(HStringReference&& other) throw();
```

### <a name="parameters"></a>參數

*sizeDest*  
樣板參數，指定目的地的大小**HStringReference**緩衝區。

*str*  
寬字元字串的參考。

*Len*  
最大長度*str*来使用這項作業中的參數緩衝區。 如果*len*參數未指定，整個*str*參數使用。 如果*len*大於*sizeDest*， *len*設定為*sizeDest*-1。

*other*  
另一個**HStringReference**物件。

## <a name="remarks"></a>備註

第一個建構函式初始化新**HStringReference**大小參數相同的物件*str*。

第二個建構函式初始化新**HStringReference**物件的參數大小 specifeid *len*。

第三個建構函式初始化新**HStringReference**的值的物件*其他*參數，然後終結*其他*參數。

## <a name="requirements"></a>需求

**標頭：** corewrappers.h

**命名空間：** Microsoft::WRL::Wrappers

## <a name="see-also"></a>另請參閱

[HStringReference 類別](../windows/hstringreference-class.md)