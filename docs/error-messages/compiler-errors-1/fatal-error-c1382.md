---
title: 嚴重錯誤 C1382
ms.date: 11/04/2016
f1_keywords:
- C1382
helpviewer_keywords:
- C1382
ms.assetid: 7a100f8c-3179-4927-a2f1-98de4c753850
ms.openlocfilehash: 2b7f6fd878f0d0ba6cde19a3a316a01c390e954a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62228560"
---
# <a name="fatal-error-c1382"></a>嚴重錯誤 C1382

產生 'obj' 後已經重建 PCH 檔案 'file'。 請重建此物件

使用時[/LTCG](../../build/reference/ltcg-link-time-code-generation.md)，編譯器偵測到較 CIL.obj 指向它的.pch 檔案。 CIL.obj 檔案中的資訊已過期。 重建物件。

如果您使用編譯，也會發生 C1382 **/Yc**，但同時也傳遞多個來源的程式碼檔案給編譯器。  若要解決，請勿使用 **/Yc**時將多個來源的程式碼檔案傳遞至編譯器。  如需詳細資訊，請參閱 < [/Yc （建立先行編譯標頭檔）](../../build/reference/yc-create-precompiled-header-file.md)。