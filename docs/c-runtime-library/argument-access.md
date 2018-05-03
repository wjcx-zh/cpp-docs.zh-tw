---
title: 引數存取 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2018
ms.technology:
- cpp-standard-libraries
ms.topic: article
f1_keywords:
- c.arguments
dev_langs:
- C++
helpviewer_keywords:
- argument access macros [C++]
- variable-length argument lists
ms.assetid: 7046ae34-a0ec-44f0-815d-3209492a3e19
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: afef1300637f7a31755eb9408f9d33d9504475a1
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="argument-access"></a>引數存取

**va_arg**、**va_end** 和 **va_start** 巨集能在引數數目為變數時，提供函式引數的存取。 這些巨集定義在 \<stdarg.h> 以便與 ANSI C 相容，以及定義在 \<varargs.h> 以便與 UNIX System V 相容。

## <a name="argument-access-macros"></a>引數存取巨集

|巨集|使用|
|-----------|-------------------------------|
|[va_arg](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)|從清單中擷取引數|
|[va_end](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)|重設指標|
|[va_start](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)|將指標設定至引數清單的開頭|

## <a name="see-also"></a>另請參閱

[依類別排序的通用 C 執行階段常式](../c-runtime-library/run-time-routines-by-category.md)
