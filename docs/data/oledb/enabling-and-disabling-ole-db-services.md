---
title: 啟用和停用 OLE DB 服務 |Microsoft 文件
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
ms.openlocfilehash: 785997cafec76bfa438382ace6930d53c31c4dc9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33099468"
---
# <a name="enabling-and-disabling-ole-db-services"></a>啟用和停用 OLE DB 服務
OLE DB 服務元件管理員會比較所支援的要判斷個別的服務元件是否無法叫用來滿足取用者要求的擴充的功能的提供者取用者指定的屬性。 例如，如果應用程式要求可捲動資料指標，提供者只支援順向資料指標，服務元件管理員會叫用用戶端資料指標引擎服務元件，以提供可捲動的功能。 如果應用程式依賴預設提供者的資料列集上支援的擴充功能和應用程式未明確設定要求的功能，功能可能不會出現在資料列集傳回用戶端上的屬性資料指標引擎。 若要互通，應用程式應該設定屬性，以明確地要求擴充的功能所需。  
  
 在某些情況下，可能必須停用個別的 OLE DB 服務，才能搭配現有的應用程式，讓提供者特性的相關假設。 OLE DB 服務提供了可停用個別的服務或根據連接的連接，或使用單一提供者的所有應用程式的所有服務。  
  
## <a name="see-also"></a>另請參閱  
 [OLE DB 資源共用和服務](../../data/oledb/ole-db-resource-pooling-and-services.md)