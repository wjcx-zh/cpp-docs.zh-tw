---
title: 編譯器警告 (層級 1) C4086
ms.date: 11/04/2016
f1_keywords:
- C4086
helpviewer_keywords:
- C4086
ms.assetid: 9248831b-22bf-47af-8684-bfadb17e94fc
ms.openlocfilehash: 77a3675bed99333031131573201d4be38240f488
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62256305"
---
# <a name="compiler-warning-level-1-c4086"></a>編譯器警告 (層級 1) C4086

pragma 參數必須為 '1'、'2'、'4'、'8' 或 '16'

pragma 參數沒有必要值 (1、2、4、8 或 16)。

## <a name="example"></a>範例

```
// C4086.cpp
// compile with: /W1 /LD
#pragma pack( 3 ) // C4086
```