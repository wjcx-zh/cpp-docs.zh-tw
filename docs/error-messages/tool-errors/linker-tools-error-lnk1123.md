---
title: "連結器工具錯誤 LNK1123 |Microsoft 文件"
ms.custom: 
ms.date: 12/29/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK1123
dev_langs: C++
helpviewer_keywords: LNK1123
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 90d46a97e27d43f97bfabd1b8ff5eab873c602a3
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/03/2018
---
# <a name="linker-tools-error-lnk1123"></a>連結器工具錯誤 LNK1123

> 轉換至 COFF 期間失敗：檔案無效或損毀

輸入檔必須具有通用物件檔案格式 (COFF) 格式。 如果輸入檔不是 COFF，則連結器會自動嘗試將 32 位元 OMF 物件，轉換為 COFF，或者執行 CVTRES.EXE，以轉換資源檔。 此訊息指出連結器無法轉換檔案。 當使用 Visual Studio、Windows Development Kit 或 .NET FrameworK 其他安裝的不相容版本 CVTRES.EXE 時，也可能會發生此情況。

> [!NOTE]
> 如果您使用舊版 Visual Studio，則可能不支援自動轉換。

## <a name="to-fix-the-problem"></a>修復問題

- 套用適用於您的 Visual Studio 版本的所有 Service Pack 和更新。 這對於 Visual Studio 2010 尤其重要。

- 請嘗試在已停用累加連結下進行建置。 在功能表列上，依序選擇 [專案] 和 [屬性]。 在**屬性頁**對話方塊方塊中，展開 **組態屬性**，**連結器**。 值變更**啟用累加連結**至**否**。

- 驗證在 PATH 環境變數中找到的 CVTRES.EXE 版本與建置工具的版本相符，或者與專案所使用的平台工具組版本相符。

- 請嘗試關閉內嵌資訊清單選項。 在功能表列上，依序選擇 [專案] 和 [屬性]。 在**屬性頁**對話方塊方塊中，展開 **組態屬性**，**資訊清單工具**，**輸入和輸出**。 值變更**內嵌資訊清單**至**否**。

- 請確認檔案類型有效。 例如，確保 OMF 物件是 32 位元而不是 16 位元。 如需詳細資訊，請參閱[。Obj 檔做為連結器輸入](../../build/reference/dot-obj-files-as-linker-input.md)和[PE 格式](https://msdn.microsoft.com/library/windows/desktop/ms680547)。

- 請確認檔案未損毀。 若有需要，請重建它。

## <a name="see-also"></a>另請參閱

[.Obj 檔作為連結器輸入](../../build/reference/dot-obj-files-as-linker-input.md)  
[EDITBIN 參考](../../build/reference/editbin-reference.md)  
[DUMPBIN 參考](../../build/reference/dumpbin-reference.md)  
