---
title: 一般 MBCS 程式設計的建議
ms.date: 11/04/2016
f1_keywords:
- _mbcs
helpviewer_keywords:
- MBCS [C++], dialog box fonts
- MS Shell Dlg
- MBCS [C++], programming
- dialog boxes [C++], fonts
ms.assetid: 7b541235-f3e5-4af0-b2c2-a0112cd5fbfb
ms.openlocfilehash: 0ff15244f4e93ecd2913fa825e8b5c351c7ff84d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50501838"
---
# <a name="general-mbcs-programming-advice"></a>一般 MBCS 程式設計的建議

使用下列秘訣：

- 為彈性，請使用執行階段巨集這類`_tcschr`和`_tcscpy`盡可能。 如需詳細資訊，請參閱 < [Tchar.h 中的泛型文字對應](../text/generic-text-mappings-in-tchar-h.md)。

- 使用 C 執行階段`_getmbcp`函式可取得目前的字碼頁的相關資訊。

- 不要重複使用字串資源。 目標語言、 根據指定的字串可能會有不同的意義時轉譯。 比方說，「 檔案 」，在應用程式的主功能表可能會以不同的方式轉譯，從 [檔案] 對話方塊中的字串。 如果您需要使用多個字串具有相同名稱，請在每個使用不同的字串識別碼。

- 您可能想要了解您的應用程式是否在 mbcs 的作業系統上執行。 若要這樣做，請在程式啟動時; 中設定旗標請勿依賴的 API 呼叫。

- 在設計對話方塊時，允許大約 30%結尾的 MBCS 轉譯的靜態文字控制項的額外空間。

- 因為有些字型不是在所有的系統上使用，則會為您的應用程式中，選擇字型時請小心。

- 當選取對話方塊的字型，使用[MS Shell Dlg](/windows/desktop/Intl/using-ms-shell-dlg-and-ms-shell-dlg-2)而不是 MS Sans Serif 或新細明體。 MS Shell Dlg 會取代正確的字型，由系統建立對話方塊之前。 使用 MS Shell Dlg，可確保作業系統來應付這種字型中的任何變更會自動提供。 （MFC 取代 MS Shell Dlg DEFAULT_GUI_FONT 或 Windows 95、 Windows 98 和 Windows NT 4 的系統字型因為這些系統未正確處理 MS Shell Dlg。）

- 在設計您的應用程式時，決定您可以當地語系化的字串。 如果在有疑問，假設任何給定的字串將會當地語系化。 此情況下，請勿使用無法混合可當地語系化的字串。

## <a name="see-also"></a>另請參閱

[MBCS 程式設計提示](../text/mbcs-programming-tips.md)<br/>
[增量和遞減指標](../text/incrementing-and-decrementing-pointers.md)