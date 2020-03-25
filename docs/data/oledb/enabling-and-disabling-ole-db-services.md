---
title: 啟用和停用 OLE DB 服務
ms.date: 10/29/2018
helpviewer_keywords:
- OLE DB services [OLE DB], enabling and disabling
- service providers [OLE DB]
ms.assetid: 445f97eb-32a8-41c2-ad26-1169f78a074f
ms.openlocfilehash: 3016126d09b39ec74f4acb758a2176be05052648
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210960"
---
# <a name="enabling-and-disabling-ole-db-services"></a>啟用和停用 OLE DB 服務

OLE DB 服務元件管理員會將取用者所指定的屬性，與提供者所支援的屬性進行比較，以判斷是否可以使用個別的服務元件來滿足取用者要求的擴充功能。 例如，如果應用程式要求可滾動的資料指標，而提供者只支援順向資料指標，則服務元件管理員會使用用戶端資料指標引擎服務元件來提供可滾動的功能。 如果應用程式依賴提供者資料列集上預設支援的擴充功能，而應用程式未明確設定屬性來要求該功能，則此功能可能不會出現在用戶端所傳回的資料列集上資料指標引擎。 若要互通，應用程式應該一律設定屬性，以便在需要時明確要求擴充功能。

在某些情況下，可能需要停用個別的 OLE DB 服務，才能與對提供者特性的假設相關的現有應用程式順利運作。 OLE DB 服務可讓您停用個別服務或所有服務，不論是以連線為基礎，或使用單一提供者的所有應用程式。

## <a name="see-also"></a>另請參閱

[OLE DB 資源共用和服務](../../data/oledb/ole-db-resource-pooling-and-services.md)
