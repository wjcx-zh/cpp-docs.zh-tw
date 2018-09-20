---
title: 'typeof 變成 t:: typeid |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- typeid operator
- __typeof keyword
- typeid keyword [C++]
ms.assetid: 6a0d35a7-7a1a-4070-b187-cff37cfdc205
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 4433061fceef455685b6588c81c8c2e434253433
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46374668"
---
# <a name="typeof-goes-to-ttypeid"></a>typeof 變成 T::typeid

`typeof`用於 Managed Extensions for c + + 已被取代的運算子`typeid`Visual c + + 中的關鍵字。

在受管理的擴充功能`__typeof()`運算子會傳回相關聯`Type*`物件時傳遞的 managed 型別名稱。 例如: 

```
// Creates and initializes a new Array instance.
Array* myIntArray =
   Array::CreateInstance( __typeof(Int32), 5 );
```

在新語法中，`__typeof`其他形式的已取代`typeid`傳回`Type^`指定 managed 型別時。

```
// Creates and initializes a new Array instance.
Array^ myIntArray =
   Array::CreateInstance( Int32::typeid, 5 );
```

## <a name="see-also"></a>另請參閱

[一般的語言變更 (C++/CLI)](../dotnet/general-language-changes-cpp-cli.md)<br/>
[typeid](../windows/typeid-cpp-component-extensions.md)