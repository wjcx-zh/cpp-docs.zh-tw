---
title: raw_interfaces_only
ms.date: 11/04/2016
f1_keywords:
- raw_interfaces_only
helpviewer_keywords:
- raw_interfaces_only attribute
ms.assetid: 87056c6d-3f34-4248-af58-f5775a35bfb7
ms.openlocfilehash: 48133b85ccb5ddb8de8e6cb614d41cde22dac66b
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59028256"
---
# <a name="rawinterfacesonly"></a>raw_interfaces_only
**C++特定**

隱藏的錯誤處理的包裝函式產生及[屬性](../cpp/property-cpp.md)使用這些包裝函式的宣告。

## <a name="syntax"></a>語法

```
raw_interfaces_only
```

## <a name="remarks"></a>備註

**Raw_interfaces_only**屬性也會造成用於命名非屬性函式會移除預設前置詞。 一般來說，前置詞是**raw_**。 如果指定這個屬性，函式名稱會直接來自類型程式庫。

這個屬性只能讓您公開類型程式庫中的低階內容。

**結束C++特定**

## <a name="see-also"></a>另請參閱

[#import 屬性](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import 指示詞](../preprocessor/hash-import-directive-cpp.md)