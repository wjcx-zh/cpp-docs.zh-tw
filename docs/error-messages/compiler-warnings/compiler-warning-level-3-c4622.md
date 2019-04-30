---
title: 編譯器警告 (層級 3) C4622
ms.date: 11/04/2016
f1_keywords:
- C4622
helpviewer_keywords:
- C4622
ms.assetid: d3c879f0-4492-4f4b-b26d-230993f3a933
ms.openlocfilehash: 88a41c7f9edb1d2a9f6d4547336a77bd5e362882
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401744"
---
# <a name="compiler-warning-level-3-c4622"></a>編譯器警告 (層級 3) C4622

覆寫在目的檔中建立先行編譯標頭檔期間產生的偵錯資訊: 'file'

所指定檔案中的 CodeView 資訊在使用 [/Yu](../../build/reference/yu-use-precompiled-header-file.md) (使用先行編譯標頭檔) 選項編譯時遺失。

建立或使用先行編譯標頭檔時，請重新命名物件檔案 (使用 [/Fo](../../build/reference/fo-object-file-name.md))，或者使用新的物件檔案進行連結。