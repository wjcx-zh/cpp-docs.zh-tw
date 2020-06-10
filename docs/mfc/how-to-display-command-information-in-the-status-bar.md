---
title: 如何：在狀態列中顯示命令資訊
ms.date: 11/04/2016
helpviewer_keywords:
- prompts [MFC]
- displaying command status [MFC]
- status bars [MFC], message area
- status bars [MFC], displaying command information
ms.assetid: de895cbe-61ee-46bf-9787-76b247527d6d
ms.openlocfilehash: bff5d5b20ecc9b20b7b1e8335cda34d582441425
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84622539"
---
# <a name="how-to-display-command-information-in-the-status-bar"></a>如何：在狀態列中顯示命令資訊

當您執行應用程式精靈來建立應用程式的基本架構時，您可以支援工具列和狀態列。 應用程式精靈中只有一個選項支援兩者。 當狀態列出現時，應用程式會在使用者將指標移至功能表的專案上方時，自動提供有用的意見反應。 反白顯示功能表項目時，應用程式會自動在狀態列中顯示提示字串。 例如，當使用者將指標移至 [**編輯**] 功能表上的 [**剪**下] 命令上方時，狀態列可能會顯示「剪下選取專案，並將其放在剪貼簿」上。 提示可協助使用者瞭解功能表項目的用途。 這也適用于使用者按一下工具列按鈕時。

您可以為新增至程式的功能表項目定義提示字串，藉此加入此狀態列說明。 若要這樣做，當您在功能表編輯器中編輯功能表項目的屬性時，請提供提示字串。 您定義的字串會儲存在應用程式資源檔中;它們的識別碼與它們所說明的命令相同。

根據預設，應用程式精靈會新增**AFX_IDS_IDLEMESSAGE**，也就是標準「就緒」訊息的識別碼，這會在程式等候新訊息時顯示。 如果您在應用程式精靈中指定 [即時線上說明] 選項，則訊息會變更為「如需協助，請按 F1」。

## <a name="see-also"></a>另請參閱

[訊息處理和對應](message-handling-and-mapping.md)
