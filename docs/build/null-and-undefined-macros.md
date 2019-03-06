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
ms.openlocfilehash: cf2dce2132cc1e7065cb0b93f1debd403f7a8342
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57417225"
---
# <a name="null-and-undefined-macros"></a>Null 和未定義的巨集

Null 和未定義的巨集展開成 null 的字串，但為 null 的字串所定義的巨集視為已定義前置處理運算式中。 若要定義巨集做為 null 的字串，指定任何字元除外命令列或指令檔中的等號 （=） 後面的空格或定位字元，且將 null 字串或定義括在雙引號 ("")。 若要取消定義巨集，使用 **！UNDEF。** 如需詳細資訊，請參閱 < [Makefile 前置處理指示詞](../build/makefile-preprocessing-directives.md)。

## <a name="see-also"></a>另請參閱

[定義 NMAKE 巨集](../build/defining-an-nmake-macro.md)
