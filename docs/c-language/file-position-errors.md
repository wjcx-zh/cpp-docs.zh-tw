---
title: 檔案位置錯誤
ms.date: 11/04/2016
helpviewer_keywords:
- file pointers [C++], file position errors
ms.assetid: d5e59d8b-08c0-4927-a338-0b2d8234ce24
ms.openlocfilehash: 3d581d86d6f08eee564feb6373a623512085ccca
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62233653"
---
# <a name="file-position-errors"></a>檔案位置錯誤

**ANSI 4.9.9.1, 4.9.9.4**：失敗時，`fgetpos` 或 `ftell` 函式要將巨集 `errno` 設定成的值

當 `fgetpos` 或 `ftell` 失敗時，如果位置無效，會將 `errno` 設定為資訊清單常數 `EINVAL`，如果檔案編號錯誤則會設為 `EBADF`。 這些常數都在 ERRNO.H 中定義。

## <a name="see-also"></a>請參閱

[程式庫函式](../c-language/library-functions.md)
