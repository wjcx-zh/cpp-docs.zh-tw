---
title: 啟用 (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- OLE server applications [MFC], activation
- OLE items [MFC], visual editing
- activation [MFC]
- OLE [MFC], in-place activation
- OLE [MFC], activation
- in-place activation, embedded and linked items
- activating objects
- visual editing, activation
- visual editing
- documents [MFC], OLE
- embedded objects [MFC]
- OLE [MFC], editing
- in-place activation
- activation [MFC], embedded OLE items
- OLE activation [MFC]
ms.assetid: ed8357d9-e487-4aaa-aa6b-2edc4de25dfa
ms.openlocfilehash: a6009e5209ce71c6eed28faff2f55792a64de408
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62392930"
---
# <a name="activation-c"></a>啟用 (C++)

這篇文章說明中視覺化編輯 OLE 項目啟用的角色。 使用者已在容器文件中內嵌 OLE 項目之後，它可能需要使用。 若要這樣做，使用者按兩下項目，該項目就會啟動。 編輯啟用最常見的活動。 許多目前 OLE 項目，進行編輯，啟動時將導致變更以反映伺服器應用程式所建立的項目屬於目前的框架視窗的功能表和工具列。 此行為，已知為就地啟用，可讓使用者編輯任何複合文件中的內嵌項目，而不需要離開容器文件視窗。

它也是可以編輯個別視窗中的內嵌的 OLE 項目。 如果在容器或伺服器應用程式不支援就地啟用，這將會發生。 在此情況下，當使用者按兩下內嵌項目時，伺服器應用程式會啟動另一個視窗中，內嵌的項目會顯示為自己的文件。 使用者編輯此視窗中的項目。 完成編輯時，使用者就會關閉伺服器應用程式，並傳回容器應用程式。

或者，使用者可以選擇 「 開啟編輯 」 搭配 **\<物件 > 開啟** 命令 **編輯**功能表。 這會開啟另一個視窗物件。

> [!NOTE]
>  編輯內嵌在另一個視窗中的項目是第 1 版的 OLE 中的標準行為，有些 OLE 應用程式可能支援的編輯這個樣式。

在就地啟用升級文件為中心的方法，來建立文件。 使用者可以在複合文件視為單一實體，在其上運作，而不需要應用程式之間切換。 不過，在就地啟用只適用於內嵌的項目，不適用於連結的項目： 必須在個別視窗中編輯它們。 這是因為連結的項目實際上儲存在不同的位置。 編輯連結的項目會儲存資料的資料，也就是實際的內容中進行。 編輯連結的項目，在個別視窗中會提醒使用者資料屬於另一個文件。

MFC 不支援巢狀的就地啟用。 如果您建立容器/伺服器應用程式和容器/伺服器內嵌在另一個容器和就地啟用，它無法就地啟用內嵌在它的物件。

當使用者按兩下它，在內嵌項目會發生什麼情況取決於項目中定義的動詞命令。 如需資訊，請參閱[啟用：動詞](../mfc/activation-verbs.md)。

## <a name="see-also"></a>另請參閱

[OLE](../mfc/ole-in-mfc.md)<br/>
[容器](../mfc/containers.md)<br/>
[伺服器](../mfc/servers.md)
