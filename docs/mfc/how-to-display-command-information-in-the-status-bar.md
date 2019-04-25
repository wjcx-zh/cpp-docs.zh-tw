---
title: HOW TO：在狀態列中顯示命令資訊
ms.date: 11/04/2016
helpviewer_keywords:
- prompts [MFC]
- displaying command status [MFC]
- status bars [MFC], message area
- status bars [MFC], displaying command information
ms.assetid: de895cbe-61ee-46bf-9787-76b247527d6d
ms.openlocfilehash: c93787b3799306d6008299e7c1be6e429bc4c2d9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62160285"
---
# <a name="how-to-display-command-information-in-the-status-bar"></a>HOW TO：在狀態列中顯示命令資訊

當您執行應用程式精靈，以建立您的應用程式的基本架構時，您可以支援工具列和狀態列。 同時支援應用程式精靈 中的一個選項。 狀態列，則應用程式，使用者將指標移項目在功能表上，會自動提供實用的意見反應。 反白顯示的功能表項目時，應用程式會將提示的字串會自動顯示在狀態列中。 例如，當使用者將指標移**剪下**命令**編輯** 功能表中，狀態 列可能會在訊息區域，狀態列的顯示 「 剪下選取項目和將它放在剪貼簿 」。 提示可協助使用者了解的功能表項目的。 這也適用於當使用者按一下工具列按鈕。

您可以定義提示的字串，您將新增至程式的功能表項目，以加入此狀態列說明。 若要這樣做，提供提示的字串，當您編輯功能表編輯器中的功能表項目的屬性。 您所定義的字串會儲存在應用程式資源檔案中;它們有相同的識別碼，這些主題會說明的命令。

根據預設，加入應用程式精靈**AFX_IDS_IDLEMESSAGE**，標準的 「 準備 」 訊息，這在程式等待新訊息時所顯示的識別碼。 如果您在應用程式精靈中指定的即時線上說明 選項，訊息會變更為 「 的說明，請按 f1 鍵 」。

## <a name="see-also"></a>另請參閱

[訊息處理和對應](../mfc/message-handling-and-mapping.md)
