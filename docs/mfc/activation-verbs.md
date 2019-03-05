---
title: 啟用：動詞命令
ms.date: 11/04/2016
helpviewer_keywords:
- verbs [MFC]
- OLE [MFC], activation
- edit verb [MFC]
- activation [MFC], verbs
- OLE [MFC], editing
- Primary verb [MFC]
- OLE activation {MFC]
ms.assetid: eb56ff23-1de8-43ad-abeb-dc7346ba7b70
ms.openlocfilehash: baf8e0ac3527407b2e5ba77dfdf3921419217fd7
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57267910"
---
# <a name="activation-verbs"></a>啟用：動詞命令

這篇文章說明在 OLE 中的角色主要和次要的動詞命令 play[啟用](../mfc/activation-cpp.md)。

通常，按兩下內嵌項目可讓使用者編輯它。 不過，某些項目都無法運作這種方式。 例如，按兩下 錄音機 」 應用程式所建立的項目不會開啟伺服器在不同的視窗;相反地，它會播放音效。

這項行為差異的原因是 錄音機 」 項目都具有不同 「 主要動詞。 」 主要的動詞命令是在使用者按兩下 OLE 項目時所執行的動作。 對於大部分的 OLE 項目類型，主要的動詞命令是編輯、 啟動建立此項目的伺服器。 針對某些類型的項目，例如 錄音機 」 項目，主要的動詞命令是播放。

許多 OLE 項目類型支援只有一個指令動詞，並編輯是最常見的方法。 不過，某些項目類型支援多個動詞命令。 例如，項目支援的錄音機 」 編輯以次要動作。

經常使用的另一個指令動詞為 Open。 Open 動詞等同於編輯，但在另一個視窗中啟動伺服器應用程式。 當容器應用程式或伺服器應用程式不支援就地啟用，則應該使用此動詞命令。

必須透過子功能表命令叫用主要的動詞命令以外的任何動作，選取項目時。 此子功能表包含項目所支援的所有動詞命令，且通常是達到所*typename* **物件**命令**編輯**功能表。 如需*typename* **物件**命令，請參閱文章[功能表和資源：容器新增](../mfc/menus-and-resources-container-additions.md)。

伺服器應用程式支援的動詞會列在 Windows 註冊資料庫。 如果您的伺服器應用程式撰寫 Mfc 程式庫，它將在伺服器啟動時自動註冊所有動詞命令。 如果沒有，您應該在伺服器應用程式的初始化階段期間進行註冊。 如需詳細資訊，請參閱文章[註冊](../mfc/registration.md)。

## <a name="see-also"></a>另請參閱

[啟動](../mfc/activation-cpp.md)<br/>
[容器](../mfc/containers.md)<br/>
[伺服器](../mfc/servers.md)
