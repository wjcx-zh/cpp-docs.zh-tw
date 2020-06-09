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
ms.openlocfilehash: 47640a59180348bd3513013b65029a775545e211
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619176"
---
# <a name="activation-c"></a>啟用 (C++)

本文說明在 OLE 專案的視覺編輯中啟用的角色。 在使用者將 OLE 專案內嵌于容器檔案之後，可能需要使用它。 若要這麼做，使用者可以按兩下專案，這會啟動該專案。 最常用的啟用活動是編輯。 許多目前的 OLE 專案在啟用以供編輯時，會導致目前框架視窗中的功能表和工具列變更，以反映屬於建立專案之伺服器應用程式的物件。 這種行為稱為「就地啟用」，可讓使用者編輯複合檔案中的任何內嵌專案，而不需要離開容器檔案的視窗。

您也可以在另一個視窗中編輯內嵌的 OLE 專案。 如果容器或伺服器應用程式不支援就地啟用，就會發生這種情況。 在此情況下，當使用者按兩下內嵌專案時，伺服器應用程式會在另一個視窗中啟動，而內嵌專案會顯示為其本身的檔。 使用者會編輯此視窗中的專案。 完成編輯時，使用者會關閉伺服器應用程式，並返回容器應用程式。

或者，使用者可以使用 [**編輯**] 功能表上的 [ ** \<object> 開啟**] 命令，選擇 [開啟編輯]。 這會在另一個視窗中開啟物件。

> [!NOTE]
> 在另一個視窗中編輯內嵌專案是 OLE 第1版中的標準行為，有些 OLE 應用程式可能只支援這種編輯樣式。

就地啟用會將以檔為中心的方法升級為檔建立。 使用者可以將複合檔案視為單一實體，而不需要在應用程式之間切換，就能處理它。 不過，就地啟用僅適用于內嵌專案，不適用於連結專案：必須在不同的視窗中編輯。 這是因為連結的專案實際上是儲存在不同的位置。 連結專案的編輯會在實際的資料內容中進行，也就是資料的儲存位置。 在個別視窗中編輯連結專案，會提醒使用者資料屬於另一份檔。

MFC 不支援嵌套的就地啟用。 如果您建立容器/伺服器應用程式，而且該容器/伺服器內嵌在另一個容器中並就地啟用，它就不能就地啟用內嵌的物件。

當使用者按兩下內嵌專案時，會發生什麼事，這取決於為專案定義的動詞。 如需相關資訊，請參閱[啟用：動詞](activation-verbs.md)。

## <a name="see-also"></a>另請參閱

[OLE](ole-in-mfc.md)<br/>
[容器](containers.md)<br/>
[伺服器](servers.md)
