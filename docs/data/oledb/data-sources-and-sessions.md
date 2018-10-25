---
title: 資料來源和工作階段 |Microsoft Docs
ms.custom: ''
ms.date: 10/22/2018
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- data sources [C++], OLE DB
- connections [C++], data source
- OLE DB consumer templates [C++], data sources
ms.assetid: 6ee52216-e082-4869-a1d6-ce561cfb76e5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 0a6cb4e27f8a248b0b90454acb782b3b8994abc4
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50056031"
---
# <a name="data-sources-and-sessions"></a>資料來源和工作階段

下圖顯示連接和存取資料來源所支援的類別。 每個類別根據標準的 OLE DB 元件實作。

![資料來源和工作階段類別](../../data/oledb/media/vcdatasourcesessionclasses.gif "vcdatasourcesessionclasses")資料來源和工作階段類別

這些類別是：

- [CDataSource](../../data/oledb/cdatasource-class.md)這個類別會具現化資料來源物件，以建立和管理透過 OLE DB 提供者的資料來源的連接。 資料來源需要資訊，例如資料來源位址和驗證資訊的連接字串的形式。

   另外值得注意的是，協助程式類別[CEnumerator](../../data/oledb/cenumerator-class.md)通常用來取得一份可用的系統上註冊的提供者建立任何連線之前。 這可讓您選取做為資料來源的提供者。 例如，**資料連結屬性** 對話方塊中會使用這個類別上填入 seznam zprostředkovatelů**提供者** 索引標籤。它等同於`SQLBrowseConnect`或`SQLDriverConnect`函式。

- [CSession](../../data/oledb/csession-class.md)這個類別會具現化工作階段物件，代表資料來源的單一存取工作階段。 不過，您可以建立多個工作階段上的資料來源。 每個工作階段，您可以建立從資料來源存取資料的資料列集、 命令和其他物件。 工作階段處理的交易。

## <a name="see-also"></a>另請參閱

[OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)