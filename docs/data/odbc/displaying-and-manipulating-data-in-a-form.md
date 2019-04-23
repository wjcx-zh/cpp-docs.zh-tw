---
title: 顯示和操作表單中的資料
ms.date: 11/04/2016
helpviewer_keywords:
- forms [C++], displaying data
- displaying data [C++], forms
- ODBC [C++], forms
- record views [C++], displaying data
- data [MFC]
- data [MFC], displaying in a form
ms.assetid: c56185c4-12cb-40b1-b499-02b29ea83e3a
ms.openlocfilehash: e50c433e701fbae2e607d79d7abb34efe8eba5b5
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59033744"
---
# <a name="displaying-and-manipulating-data-in-a-form"></a>顯示和操作表單中的資料

許多資料存取應用程式選取的資料，並顯示在表單中的欄位。 Database 類別[CRecordView](../../mfc/reference/crecordview-class.md)可讓您[CFormView](../../mfc/reference/cformview-class.md)直接連接到資料錄集物件的物件。 使用資料錄檢視[對話資料交換 (DDX)](../../mfc/dialog-data-exchange-and-validation.md)將從資料錄集內，將目前資料錄的欄位的值移到表單上的控制項，並將更新的資訊移回資料錄集。 資料錄集，接著會使用其欄位資料成員資料表中的對應資料行之間移動資料，資料來源上的資料錄欄位交換 (RFX)。

您可以使用 MFC 應用程式精靈或**加入類別**(如中所述[加入 MFC ODBC 消費者](../../mfc/reference/adding-an-mfc-odbc-consumer.md)) 一起建立的檢視類別和其相關聯的資料錄集類別。

當您關閉文件時，就會遭到銷毀資料錄檢視以及其資料錄集。 如需有關資料錄檢視的詳細資訊，請參閱 <<c0> [ 資料錄檢視](../../data/record-views-mfc-data-access.md)。 如需 RFX 的詳細資訊，請參閱[資料錄欄位交換 (RFX)](../../data/odbc/record-field-exchange-rfx.md)。

## <a name="see-also"></a>另請參閱

[ODBC 和 MFC](../../data/odbc/odbc-and-mfc.md)