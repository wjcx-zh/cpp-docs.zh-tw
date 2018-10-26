---
title: 啟用和停用 OLE DB 服務 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB services [OLE DB], enabling and disabling
- service providers [OLE DB]
ms.assetid: 445f97eb-32a8-41c2-ad26-1169f78a074f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 72c890b94d84d170bb3ee01bd02d08fc00f9aa04
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50068217"
---
# <a name="enabling-and-disabling-ole-db-services"></a>啟用和停用 OLE DB 服務

OLE DB 服務元件管理員比較所要判斷個別的服務元件是否可以叫用來滿足取用者要求的擴充的功能的提供者支援取用者指定的屬性。 例如，如果應用程式要求可捲動資料指標，提供者只支援順向資料指標服務元件管理員會叫用用戶端資料指標引擎的服務元件，可提供可捲動的功能。 如果應用程式依賴預設提供者的資料列集上支援的擴充功能和應用程式沒有明確設定要求的功能，功能可能不會出現在資料列集傳回用戶端上的屬性資料指標引擎。 若要具互通性，應用程式應該一律設定屬性，以明確地要求 擴充的功能在需要時。

在某些情況下，可能必須停用個別的 OLE DB 服務，適合搭配現有的應用程式，讓提供者的特性的相關假設。 OLE DB 服務提供停用個別的服務或所有服務，不論是根據連接的連接，或使用單一提供者的所有應用程式的功能。

## <a name="see-also"></a>另請參閱

[OLE DB 資源共用和服務](../../data/oledb/ole-db-resource-pooling-and-services.md)