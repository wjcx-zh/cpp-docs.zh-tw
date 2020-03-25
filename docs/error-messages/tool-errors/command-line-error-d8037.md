---
title: 命令列錯誤 D8037
ms.date: 11/04/2016
f1_keywords:
- D8037
helpviewer_keywords:
- D8037
ms.assetid: acddaaa0-bd84-426f-a37b-8f680b379c9d
ms.openlocfilehash: ed6778861c89bb9755087c4d58f094a57d5f760f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80196855"
---
# <a name="command-line-error-d8037"></a>命令列錯誤 D8037

無法建立暫存 il 檔案;清除舊 il 檔案的臨時目錄

空間不足，無法建立暫存編譯器中繼檔案。 若要解決這個錯誤，請移除**TMP**環境變數所指定之目錄中的任何舊 MSIL 檔案。 這些檔案的格式為 _CL_hhhhhhhh. ss，其中 h 代表隨機的十六進位數位，而 ss 代表 IL 檔案的類型。 此外，請務必使用最新的作業系統修補程式來更新您的電腦。

## <a name="see-also"></a>另請參閱

[命令列錯誤 D8000 至 D9999](../../error-messages/tool-errors/command-line-errors-d8000-through-d9999.md)<br/>
[MSVC 編譯器選項](../../build/reference/compiler-options.md)
