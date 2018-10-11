---
title: 動態集的 ODBC 驅動程式需求 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ODBC recordsets, dynasets
- drivers, for dynasets
- drivers, ODBC
- recordsets, dynasets
- dynasets
- ODBC drivers, dynasets
ms.assetid: 585cc67b-4d92-404b-9903-d769cd17badc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f6c7a9282ce1516ae3410307b74a66ba34adbcea
ms.sourcegitcommit: 3a141cf07b5411d5f1fdf6cf67c4ce928cf389c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/11/2018
ms.locfileid: "49082705"
---
# <a name="odbc-driver-requirements-for-dynasets"></a>動態集的 ODBC 驅動程式需求

在 MFC ODBC 資料庫類別中，動態集是資料錄集動態屬性;它們都能保持同步的資料來源，在某些方面。 MFC 動態集 （但不是順向資料錄集） 需要使用一致性層級 2 API 的 ODBC 驅動程式。 如果驅動程式為您[資料來源](../../data/odbc/data-source-odbc.md)符合層級 1 API 設定，您仍然可以使用可更新和唯讀快照集和順向資料錄集，但不是動態集。 不過，層級 1 的驅動程式可支援動態集，如果它支援擴充的擷取與索引鍵集驅動資料指標。  
  
在 ODBC 術語中，動態集和快照集被指資料指標。 資料指標是一種機制，用於追蹤的資料錄集中的位置。 如需有關動態集的驅動程式需求的詳細資訊，請參閱[動態集](../../data/odbc/dynaset.md)。 如需有關資料指標的詳細資訊，請參閱 <<c0> [ 開放式資料庫連接 (ODBC)](/previous-versions/windows/desktop/ms710252) MSDN 文件中的 SDK。  
  
> [!NOTE]
>  可更新的資料錄集，您的 ODBC 驅動程式必須支援任一定位的 update 陳述式或`::SQLSetPos`ODBC API 函式。 如果兩者都有支援，MFC 會使用`::SQLSetPos`為了提高效率。 或者，對於快照集，您可以使用資料指標程式庫，可提供所需的支援可更新的快照集 （靜態資料指標和定位的 update 陳述式）。  
  
## <a name="see-also"></a>另請參閱  

[ODBC 基本概念](../../data/odbc/odbc-basics.md)