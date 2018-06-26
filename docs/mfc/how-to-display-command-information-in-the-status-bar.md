---
title: 如何： 在狀態列中顯示命令資訊 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- prompts [MFC]
- displaying command status [MFC]
- status bars [MFC], message area
- status bars [MFC], displaying command information
ms.assetid: de895cbe-61ee-46bf-9787-76b247527d6d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 84f1a12dd9ca25ec19415cde42dc8ce12e515833
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2018
ms.locfileid: "36930949"
---
# <a name="how-to-display-command-information-in-the-status-bar"></a>如何：在狀態列中顯示命令資訊
當您執行應用程式精靈，以建立您的應用程式的基本架構時，您就可以支援工具列和狀態列。 同時支援應用程式精靈中的一個選項。 狀態列，則應用程式為使用者將指標移項目在功能表上，會自動提供實用的意見反應。 反白顯示的功能表項目時，應用程式會自動將提示字串顯示在狀態列中。 例如，當使用者將指標移**剪下**命令**編輯**功能表上，[狀態] 列可能會顯示"剪下選取項目並將它放在剪貼簿 」 訊息區域的 [狀態] 列中。 提示可協助使用者了解功能表項目的用途。 這也適用於當使用者按一下工具列按鈕。  
  
 您可以藉由定義提示字串加入至程式的功能表項目加入此狀態列的說明。 若要這樣做，提供提示字串，當您編輯功能表編輯器中的功能表項目的屬性。 您定義的字串會儲存在應用程式資源檔案中;它們有相同的識別碼，它們說明的命令。  
  
 根據預設，應用程式精靈加入**AFX_IDS_IDLEMESSAGE**，標準的 「 準備 」 訊息，這當程式正在等待新訊息時所顯示的識別碼。 如果您在應用程式精靈中指定即時線上說明 選項，訊息會變成 「 如需說明，請按 F1 」。  
  
## <a name="see-also"></a>另請參閱  
 [訊息處理和對應](../mfc/message-handling-and-mapping.md)

