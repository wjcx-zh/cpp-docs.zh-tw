---
title: 保留字
ms.date: 11/04/2016
f1_keywords:
- code
- CONFORMING
- DISCARDABLE
- Description
- base
- APPLOADER
- Data
- DYNAMIC
- DEV386
helpviewer_keywords:
- .def files [C++], reserved words
- def files [C++], reserved words
- linker [C++], reserved words
- reserved words [C++]
ms.assetid: 9b9f49e5-0739-45ab-a37e-81e3915ceb25
ms.openlocfilehash: 62893d4af1633bc2c89d2d6a0fa71309a0411ad5
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88836838"
---
# <a name="reserved-words"></a>保留字

連結器會保留下列單字。 只有當名稱以雙引號括住 ( "" ) 時，這些名稱才可以用來做為 [模組定義語句](module-definition-dot-def-files.md) 中的引數。

:::row:::
   :::column span="":::
      **`APPLOADER`**<sup>單</sup>\
      **`BASE`**\
      **`CODE`**\
      **`CONFORMING`**\
      **`DATA`**\
      **`DESCRIPTION`**\
      **`DEV386`**\
      **`DISCARDABLE`**\
      **`DYNAMIC`**\
      **`EXECUTE-ONLY`**\
      **`EXECUTEONLY`**\
      **`EXECUTEREAD`**\
      **`EXETYPE`**\
      **`EXPORTS`**\
      **`FIXED`**<sup>單</sup>
   :::column-end:::
   :::column span="":::
      **`FUNCTIONS`**<sup>二級</sup>\
      **`HEAPSIZE`**\
      **`IMPORTS`**\
      **`IMPURE`**<sup>單</sup>\
      **`INCLUDE`**<sup>二級</sup>\
      **`INITINSTANCE`**<sup>二級</sup>\
      **`IOPL`**\
      **`LIBRARY`**<sup>單</sup>\
      **`LOADONCALL`**<sup>單</sup>\
      **`LONGNAMES`**<sup>二級</sup>\
      **`MOVABLE`**<sup>單</sup>\
      **`MOVEABLE`**<sup>單</sup>\
      **`MULTIPLE`**\
      **`NAME`**\
      **`NEWFILES`**<sup>二級</sup>
   :::column-end:::
   :::column span="":::
      **`NODATA`**<sup>單</sup>\
      **`NOIOPL`**<sup>單</sup>\
      **`NONAME`**\
      **`NONCONFORMING`**<sup>單</sup>\
      **`NONDISCARDABLE`**\
      **`NONE`**\
      **`NONSHARED`**\
      **`NOTWINDOWCOMPAT`**<sup>單</sup>\
      **`OBJECTS`**\
      **`OLD`**<sup>單</sup>\
      **`PRELOAD`**\
      **`PRIVATE`**\
      **`PROTMODE`**<sup>二級</sup>\
      **`PURE`**<sup>單</sup>\
      **`READONLY`**
   :::column-end:::
   :::column span="":::
      **`READWRITE`**\
      **`REALMODE`**<sup>單</sup>\
      **`RESIDENT`**\
      **`RESIDENTNAME`**<sup>單</sup>\
      **`SECTIONS`**\
      **`SEGMENTS`**\
      **`SHARED`**\
      **`SINGLE`**\
      **`STACKSIZE`**\
      **`STUB`**\
      **`VERSION`**\
      **`WINDOWAPI`**\
      **`WINDOWCOMPAT`**\
      **`WINDOWS`**
   :::column-end:::
:::row-end:::

<sup>1</sup> 當連結器遇到此詞彙時，會發出警告 ( 「已忽略」 ) 。 但是，這個字仍然是保留的。

<sup>2</sup> 連結器會忽略這個字，但不發出警告。

## <a name="see-also"></a>另請參閱

- [MSVC 連結器參考](linking.md)
- [MSVC 連結器選項](linker-options.md)
