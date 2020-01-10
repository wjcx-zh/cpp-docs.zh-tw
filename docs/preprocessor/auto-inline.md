---
title: auto_inline pragma
ms.date: 08/29/2019
f1_keywords:
- auto_inline_CPP
- vc-pragma.auto_inline
helpviewer_keywords:
- pragmas, auto_inline
- auto_inline pragma
ms.assetid: f7624cd1-be76-429a-881c-65c9040acf43
ms.openlocfilehash: 59cda8cb73196215318c9570a5c067786284afaa
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216310"
---
# <a name="auto_inline-pragma"></a>auto_inline pragma

排除範圍內所定義的任何函式, 其中的**off**是指定為自動內嵌展開的候選項目。

## <a name="syntax"></a>語法

> **#pragma auto_inline (** [{ **on**  |  **off** }] **)**

## <a name="remarks"></a>備註

若要使用**auto_inline** pragma, 請將它放在函式定義的前後, 而不是內部。 Pragma 會在 pragma 出現後的第一個函式定義時立即生效。

## <a name="see-also"></a>另請參閱

[Pragma 指示詞和 __pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
