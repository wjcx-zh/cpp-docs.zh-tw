---
title: 編譯器警告 (層級 1) C4041
ms.date: 11/04/2016
f1_keywords:
- C4041
helpviewer_keywords:
- C4041
ms.assetid: 107ee9fd-4b88-4f22-a18f-a20726831095
ms.openlocfilehash: 14ea6d9cae3b490107b656153bb68815026971e1
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80164231"
---
# <a name="compiler-warning-level-1-c4041"></a>編譯器警告 (層級 1) C4041

編譯器限制 : 瀏覽器資訊超出編譯器上限，已終止輸出

瀏覽器資訊超過編譯器限制。

這個警告可能是使用 [/FR](../../build/reference/fr-fr-create-dot-sbr-file.md) (包含區域變數的瀏覽器資訊) 進行編譯所造成。

### <a name="to-fix-by-using-the-following-possible-solutions"></a>使用下列可能的解決方式來進行修正

1. 使用 /Fr (未含區域變數的瀏覽器資訊) 進行編譯。

1. 停用瀏覽器輸出 (不使用 /FR 或 /Fr 進行編譯)。
