---
title: OLE DB 資源集中化和服務 |Microsoft Docs
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
ms.openlocfilehash: c2a04d0b990906f9f124edc9dbda71d65127e4ed
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2018
ms.locfileid: "39338557"
---
# <a name="ole-db-resource-pooling-and-services"></a>OLE DB 資源集中化和服務
若要搭配 OLE DB 共用，或任何 OLE DB 服務，您的提供者必須支援所有物件的彙的總。 這是任何 OLE DB 1.5 或更新版本的提供者的需求。 最重要的是利用服務。 不支援彙總的提供者無法共用，並且會提供任何其他服務。  
  
 若要共用，提供者必須支援無限制執行緒模型。 資源集區會決定提供者的執行緒模型，根據`DBPROP_THREADMODEL`屬性。  
  
 如果提供者有可能會變更資料來源初始化的狀態時的全域連線狀態，則它應該支援對新`DBPROP_RESETDATASOURCE`屬性。 此屬性稱為之前連線重複使用，並讓提供者有機會先清除其下一步 使用之前的狀態。 如果提供者無法清除某些與連接相關聯的狀態，則可以傳回`DBPROPSTATUS_NOTSETTABLE`的屬性和連線將不會重複使用。  
  
 提供者連接至遠端資料庫，並可偵測是否應支援連線可能會遺失`DBPROP_CONNECTIONSTATUS`屬性。 這個屬性會讓 OLE DB 服務能夠偵測無作用的連線，並確定它們不會傳回給集區。  
  
 最後，自動異動登記通常不適用，除非它實作共用，就會發生相同層級。 自動交易登記為自己支援的提供者應該支援公開停用這個登記`DBPROP_INIT_OLEDBSERVICES`屬性，並停用登錄，如果`DBPROPVAL_OS_TXNENLISTMENT`取消選取。  
  
## <a name="see-also"></a>另請參閱  
 [進階的提供者技術](../../data/oledb/advanced-provider-techniques.md)