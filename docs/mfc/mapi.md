---
title: MAPI
ms.date: 11/04/2016
helpviewer_keywords:
- messaging [MFC], client applications
- enabling applications for MAPI [MFC]
- MAPI support in MFC
- e-mail [MFC], enabling
- mail [MFC], enabling your application
- MAPI, MFC
- enabling applications for mail [MFC]
ms.assetid: 193449f7-b131-4ab0-9301-8d4f6cd1e7c4
ms.openlocfilehash: a5f60e1ba8c2b68ddca312859694f532e38da965
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57279103"
---
# <a name="mapi"></a>MAPI

本文說明用戶端訊息應用程式開發人員的 Microsoft 訊息應用程式開發介面 (MAPI)。 MFC 提供類別中 MAPI 子集的支援`CDocument`但不會封裝整個 API。 如需詳細資訊，請參閱 < [MFC 中的 MAPI 支援](../mfc/mapi-support-in-mfc.md)。

MAPI 是一組擁有郵件功能和可感知郵件之應用程式函式，用來建立、操作、傳輸和儲存郵件。 它提供應用程式開發人員用於定義郵件訊息用途和內容的工具，並提供他們管理儲存郵件訊息的彈性。 MAPI 也提供應用程式開發人員可用於建立擁有郵件功能和可感知郵件之應用程式，但與基礎郵件系統無關的通用介面。

郵件用戶端提供可與 Microsoft Windows 郵件系統 (WMS) 互動的人性化介面。 這種互動通常包含要求 MAPI 相容提供者的服務，例如郵件儲存區和通訊錄。

如需 MAPI 的詳細資訊，請參閱文章中 Win32 郵件 (MAPI) 指南底下的 Windows sdk。

## <a name="in-this-section"></a>本節內容

[MFC 中的 MAPI 支援](../mfc/mapi-support-in-mfc.md)

## <a name="see-also"></a>另請參閱

[CDocument::OnFileSendMail](../mfc/reference/cdocument-class.md#onfilesendmail)<br/>
[CDocument::OnUpdateFileSendMail](../mfc/reference/cdocument-class.md#onupdatefilesendmail)<br/>
[COleDocument::OnFileSendMail](../mfc/reference/coledocument-class.md#onfilesendmail)
