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
ms.openlocfilehash: 03edba0a4336fdc147ef6dd10c7a8154aca19d3a
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616636"
---
# <a name="activation-verbs"></a>啟用：動詞命令

本文說明在 OLE[啟用](activation-cpp.md)中扮演主要和次要動詞的角色。

通常，按兩下內嵌專案可讓使用者進行編輯。 不過，某些專案的行為並不相同。 例如，按兩下以答錄機應用程式建立的專案，並不會在另一個視窗中開啟伺服器;相反地，它會播放音效。

這種行為差異的原因是，錄製器專案有不同的「主要動詞」。 主要動詞命令是使用者按兩下 OLE 專案時所執行的動作。 對於大部分類型的 OLE 專案而言，主要動詞為 Edit，這會啟動建立專案的伺服器。 對於某些類型的專案（例如，[答錄機專案]），主要動詞為 [播放]。

許多類型的 OLE 專案僅支援一個動詞，而 [編輯] 是最常見的一個。 不過，某些類型的專案支援多個動詞。 例如，「音效錄製器」專案支援 [編輯] 做為次要動詞。

經常使用的另一個動詞已開啟。 [開啟] 動詞與 [編輯] 相同，不同之處在于伺服器應用程式是在另一個視窗中啟動。 當容器應用程式或伺服器應用程式不支援就地啟用時，應該使用這個動詞命令。

選取專案時，必須透過子功能表命令叫用主要動詞以外的任何動詞。 此子功能表包含專案支援的所有動詞，而且通常是由 [**編輯**] 功能表上的 [ *typename* **物件**] 命令所到達。 如需*typename* **Object**命令的詳細資訊，請參閱文章[功能表和資源：容器新增](menus-and-resources-container-additions.md)。

伺服器應用程式支援的動詞會列在 Windows 註冊資料庫中。 如果您的伺服器應用程式是以 MFC 程式庫撰寫，它會在伺服器啟動時自動註冊所有動詞。 如果不是，您應該在伺服器應用程式的初始化階段進行註冊。 如需詳細資訊，請參閱[註冊](registration.md)一文。

## <a name="see-also"></a>另請參閱

[啟用](activation-cpp.md)<br/>
[容器](containers.md)<br/>
[伺服器](servers.md)
