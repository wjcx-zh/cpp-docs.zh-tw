---
title: 資源編譯器錯誤 RC2144
ms.date: 11/04/2016
f1_keywords:
- RC2144
helpviewer_keywords:
- RC2144
ms.assetid: 1b3ff39a-92cd-4a04-b1a3-b1fa6a805813
ms.openlocfilehash: 1b080916642fc1be4b22820668c4cb4137675425
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80191193"
---
# <a name="resource-compiler-error-rc2144"></a>資源編譯器錯誤 RC2144

PRIMARY LANGUAGE ID 不是數字

PRIMARY LANGUAGE ID 必須是十六進位語言 ID。 請參閱《執行階段程式庫參考》 中的 *[語言和國家/地區字串](../../c-runtime-library/locale-names-languages-and-country-region-strings.md)* ，以取得有效語言 ID 的清單。

如果已在 .RC 檔案中使用工具加入和刪除資源，也會發生此錯誤。 若要修正這個問題，請在文字編輯器中開啟 .RC 檔案，並以手動方式清除任何未使用的資源。
