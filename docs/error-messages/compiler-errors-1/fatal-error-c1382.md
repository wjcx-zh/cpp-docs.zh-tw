---
title: 嚴重錯誤 C1382
ms.date: 11/04/2016
f1_keywords:
- C1382
helpviewer_keywords:
- C1382
ms.assetid: 7a100f8c-3179-4927-a2f1-98de4c753850
ms.openlocfilehash: 6ed70a81c4ae2028d09b694f325f83454e99a587
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80203095"
---
# <a name="fatal-error-c1382"></a>嚴重錯誤 C1382

已重建 PCH 檔案 ' file '，因為已產生 ' obj '。 請重建此物件

使用[/ltcg](../../build/reference/ltcg-link-time-code-generation.md)時，編譯器偵測到的 .pch 檔案比指向該檔案的 CIL .obj 還新。 CIL .obj 檔案中的資訊已過期。 重建物件。

如果您使用 **/yc**進行編譯，但同時將多個原始程式碼檔案傳遞給編譯器，也可能會發生 C1382。  若要解決此問題，請不要在將多個原始程式碼檔案傳遞給編譯器時，使用 **/yc** 。  如需詳細資訊，請參閱[/yc （建立先行編譯標頭檔）](../../build/reference/yc-create-precompiled-header-file.md)。
