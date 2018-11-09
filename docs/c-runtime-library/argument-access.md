---
title: 引數存取
ms.date: 04/04/2018
f1_keywords:
- c.arguments
helpviewer_keywords:
- argument access macros [C++]
- variable-length argument lists
ms.assetid: 7046ae34-a0ec-44f0-815d-3209492a3e19
ms.openlocfilehash: 8107cffa6a2da41c38b116b2e3fe36adf6ac945f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50470404"
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
