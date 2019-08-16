---
title: 一般 MBCS 程式設計的建議
ms.date: 11/04/2016
helpviewer_keywords:
- MBCS [C++], dialog box fonts
- MS Shell Dlg
- MBCS [C++], programming
- dialog boxes [C++], fonts
ms.assetid: 7b541235-f3e5-4af0-b2c2-a0112cd5fbfb
ms.openlocfilehash: 887387220105614eb3257f008ec601a6fc0adc18
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491190"
---
# <a name="general-mbcs-programming-advice"></a>一般 MBCS 程式設計的建議

請使用下列秘訣:

- 如需彈性, 請盡可能使用執行時間宏`_tcschr` ( `_tcscpy`例如和)。 如需詳細資訊, 請參閱[tchar 中的泛型文字](../text/generic-text-mappings-in-tchar-h.md)對應。

- 使用 C 執行時間`_getmbcp`函式來取得目前字碼頁的相關資訊。

- 請勿重複使用字串資源。 視目的語言而定, 指定的字串在轉譯時可能會有不同的意義。 例如, 應用程式主功能表上的 [檔案] 可能會以不同于對話方塊中的字串 "File" 轉譯。 如果您需要使用多個具有相同名稱的字串, 請為每個使用不同的字串識別碼。

- 您可能想要瞭解您的應用程式是否在已啟用 MBCS 的作業系統上執行。 若要這麼做, 請在程式啟動時設定旗標;請勿依賴 API 呼叫。

- 設計對話方塊時, 請在適用于 MBCS 轉譯的靜態文字控制項結尾, 允許大約 30% 的額外空間。

- 選取應用程式的字型時請小心, 因為某些字型在所有系統上都無法使用。

- 選取對話方塊的字型時, 請使用[Ms Shell Dlg](/windows/win32/Intl/using-ms-shell-dlg-and-ms-shell-dlg-2) , 而不是 Ms Sans Serif 或 Helvetica。 系統會在建立對話方塊之前, 以正確的字型取代 MS Shell Dlg。 使用 MS Shell Dlg 可確保作業系統中的任何變更處理此字型都會自動提供。 (MFC 會以 DEFAULT_GUI_FONT 或 Windows 95、Windows 98 和 Windows NT 4 上的系統字型取代 MS Shell Dlg, 因為這些系統不會正確地處理 MS Shell Dlg)。

- 設計您的應用程式時, 請決定可以當地語系化的字串。 如果不確定, 則假設任何指定的字串將會當地語系化。 因此, 請不要混用可以使用不能當地語系化的字串。

## <a name="see-also"></a>另請參閱

[MBCS 程式設計提示](../text/mbcs-programming-tips.md)<br/>
[增量和遞減指標](../text/incrementing-and-decrementing-pointers.md)
