---
title: 連結器工具錯誤 LNK1123
ms.date: 12/29/2017
f1_keywords:
- LNK1123
helpviewer_keywords:
- LNK1123
ms.openlocfilehash: 31fd634291bfb0af17348197ae8a6225ac490c89
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69509908"
---
# <a name="linker-tools-error-lnk1123"></a>連結器工具錯誤 LNK1123

> 轉換至 COFF 期間失敗：檔案無效或損毀

輸入檔必須具有通用物件檔案格式 (COFF) 格式。 如果輸入檔不是 COFF，則連結器會自動嘗試將 32 位元 OMF 物件，轉換為 COFF，或者執行 CVTRES.EXE，以轉換資源檔。 此訊息指出連結器無法轉換檔案。 當使用 Visual Studio、Windows Development Kit 或 .NET FrameworK 其他安裝的不相容版本 CVTRES.EXE 時，也可能會發生此情況。

> [!NOTE]
> 如果您使用舊版 Visual Studio，則可能不支援自動轉換。

## <a name="to-fix-the-problem"></a>修復問題

- 套用適用於您的 Visual Studio 版本的所有 Service Pack 和更新。 這對於 Visual Studio 2010 尤其重要。

- 請嘗試在已停用累加連結下進行建置。 在功能表列上，依序選擇 [專案] 和 [屬性]。 在 [**屬性頁**] 對話方塊中, 展開 [設定**屬性**]、[**連結器**]。 將 [**啟用增量連結**] 的值變更為 [**否**]。

- 驗證在 PATH 環境變數中找到的 CVTRES.EXE 版本與建置工具的版本相符，或者與專案所使用的平台工具組版本相符。

- 請嘗試關閉內嵌資訊清單選項。 在功能表列上，依序選擇 [專案] 和 [屬性]。 在 [**屬性頁**] 對話方塊中, 展開 [設定**屬性**]、[**資訊清單工具**]、[**輸入和輸出**]。 將 [**內嵌資訊清單**] 的值變更為 [**否**]。

- 請確認檔案類型有效。 例如，確保 OMF 物件是 32 位元而不是 16 位元。 如需詳細資訊, 請參閱[。做為連結器輸入](../../build/reference/dot-obj-files-as-linker-input.md)和[PE 格式](/windows/win32/Debug/pe-format)的 Obj 檔案。

- 請確認檔案未損毀。 若有需要，請重建它。

## <a name="see-also"></a>另請參閱

[.Obj 檔作為連結器輸入](../../build/reference/dot-obj-files-as-linker-input.md)<br/>
[EDITBIN 參考](../../build/reference/editbin-reference.md)<br/>
[DUMPBIN 參考](../../build/reference/dumpbin-reference.md)
