---
title: TN047： 放寬資料庫異動需求 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.data
dev_langs:
- C++
helpviewer_keywords:
- TN047
ms.assetid: f93c51cf-a8c0-43d0-aa47-7bcb8333d693
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 96f3116f503ffa0ffc461ea2c1a0bdaf8947a0be
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46427013"
---
# <a name="tn047-relaxing-database-transaction-requirements"></a>TN047：放寬資料庫異動需求

這個技術提示討論 MFC ODBC 資料庫類別的交易需求，現在已過時。 在 MFC 4.2 之前的資料庫類別所需資料指標會保留在資料錄集後**CommitTrans**或是**Rollback**作業。 ODBC 驅動程式和 DBMS 並不支援此層級的資料指標保留，如果資料庫類別未啟用的交易。

從 MFC 4.2 開始，資料庫類別有寬鬆要求資料指標保留的限制。 如果此驅動程式支援它們，就會啟用交易。 不過，您現在必須檢查的效果**CommitTrans**或是**Rollback**上開啟資料錄集的作業。 請參閱成員函式[CDatabase::GetCursorCommitBehavior](../mfc/reference/cdatabase-class.md#getcursorcommitbehavior)並[CDatabase::GetCursorRollbackBehavior](../mfc/reference/cdatabase-class.md#getcursorrollbackbehavior)如需詳細資訊。

## <a name="see-also"></a>另請參閱

[依編號顯示的技術提示](../mfc/technical-notes-by-number.md)<br/>
[依分類區分的技術提示](../mfc/technical-notes-by-category.md)

