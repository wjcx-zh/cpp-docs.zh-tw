---
title: 特性指引優化錯誤 PG0165
description: 描述讀取特性指引優化（PGO）資料時的 PG0165 錯誤。
ms.date: 10/30/2019
f1_keywords:
- PG0165
helpviewer_keywords:
- PG0165
ms.assetid: e98122e7-ddee-4a2c-96b2-d232e4c65f3e
ms.openlocfilehash: c5e5c5d37f8c70a6c2a3d9f7a43c13bb46d0e25a
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626794"
---
# <a name="profile-guided-optimization-error-pg0165"></a>特性指引優化錯誤 PG0165

讀取特性指引優化資料時發生錯誤。 此錯誤可能會以數種形式出現：

> 讀取 '*檔案名 .pgd*'： ' pgd 版本不受支援（版本不符） '。

PGD 檔案僅適用于特定的編譯器工具組。 當您使用不同于用來建立*檔案名 .pgd*的編譯器時，就會產生這項錯誤。 此錯誤表示此編譯器工具組無法使用*檔案名 .pgd*的資料來優化目前的程式。 若要解決這個問題，請使用目前的編譯器工具組來重新產生*檔案名*.pgd。

> 讀取 '*檔案名 .pgd*'： ' pgd 檔案是唯讀的 '。

當 PGD 檔案在檔案系統上標示為唯讀時，就會顯示此錯誤。 若要解決此問題，請將檔案屬性變更為讀寫。
