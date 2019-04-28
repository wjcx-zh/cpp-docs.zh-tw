---
title: Null 和未定義的巨集
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, undefined macros
- Null macros in NMAKE
- macros, null and undefined
- undefined macros and NMAKE
- NMAKE program, null macros
ms.assetid: 1db4611a-1755-4328-b00f-d35365af8b6c
ms.openlocfilehash: 0f4905473dd6914547ad6ac129d34e438992c2af
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62320496"
---
# <a name="null-and-undefined-macros"></a>Null 和未定義的巨集

Null 和未定義的巨集展開成 null 的字串，但為 null 的字串所定義的巨集視為已定義前置處理運算式中。 若要定義巨集做為 null 的字串，指定任何字元除外命令列或指令檔中的等號 （=） 後面的空格或定位字元，且將 null 字串或定義括在雙引號 ("")。 若要取消定義巨集，使用 **！UNDEF。** 如需詳細資訊，請參閱 < [Makefile 前置處理指示詞](makefile-preprocessing-directives.md)。

## <a name="see-also"></a>另請參閱

[定義 NMAKE 巨集](defining-an-nmake-macro.md)
