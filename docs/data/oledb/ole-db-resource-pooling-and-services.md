---
title: OLE DB 資源集中化和服務 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- resource pooling [OLE DB], provider requirements
- OLE DB, resource pooling
- service providers [OLE DB]
- OLE DB services [OLE DB], provider requirements
- OLE DB services [OLE DB]
- OLE DB providers, resource pooling
ms.assetid: 360c36e2-25ae-4caf-8ee7-d4a6b6898f68
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: ab8c5e5a3e219da7204ef1a1b4942dc70b2f2ad2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33111181"
---
# <a name="ole-db-resource-pooling-and-services"></a>OLE DB 資源集中化和服務
若要與 OLE DB 共用，或與任何 OLE DB 服務工作，您的提供者必須支援所有物件的彙的總。 這是任何 OLE DB 1.5 或更新版本的提供者的需求。 它是利用服務的關鍵。 不支援彙總的提供者無法共用，而沒有其他服務所提供。  
  
 若要共用，提供者必須支援無限制執行緒模型。 資源集區決定提供者的執行緒模型，根據**DBPROP_THREADMODEL**屬性。  
  
 提供者具有全域連線狀態，可能會變更資料來源初始化的狀態時，它應該支援新**DBPROP_RESETDATASOURCE**屬性。 此屬性稱為之前連線已重複使用，並讓提供者有機會清除下次使用之前的狀態。 如果提供者無法清除與連接相關聯的某種狀態，則可以傳回**使用者**的屬性和連接將不會重複使用。  
  
 連接到遠端資料庫，並可偵測是否應支援連線可能會遺失提供者**DBPROP_CONNECTIONSTATUS**屬性。 這個屬性會讓 OLE DB 服務能夠偵測無作用的連線，並確定它們不會傳回至集區。  
  
 最後，自動交易登記通常無法運作除非它共用，就會發生相同的層級實作。 支援自動交易登記自己的提供者應該支援公開停用這個登記**DBPROP_INIT_OLEDBSERVICES**屬性，如果停用登記**DBPROPVAL_OS_TXNENLISTMENT**取消選取。  
  
## <a name="see-also"></a>另請參閱  
 [進階的提供者技術](../../data/oledb/advanced-provider-techniques.md)