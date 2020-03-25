---
title: 轉散發 ODBC 元件給您的客戶
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC components, redistributing
- ODBC, distributing components
- components [C++], distributing
- ODBC Administrator
- components [C++]
- components [C++], redistributing
ms.assetid: 17b065b4-a307-4b89-99ac-d05831cfab87
ms.openlocfilehash: 0d4d3948add665c54be3d3b0596a7a6fc0e414f5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212728"
---
# <a name="redistributing-odbc-components-to-your-customers"></a>轉散發 ODBC 元件給您的客戶

如果您將 ODBC 系統管理員程式的功能併入您的應用程式，則也必須將執行這些程式的檔案散發給使用者。 這些 ODBC 檔案位於視覺C++ Cd-rom 的 \OS\System 目錄中。 Redistrb. wri 檔案和相同目錄中的授權合約包含您可以重新發佈的 ODBC 檔案清單。

請參閱您打算寄送的任何 ODBC 驅動程式的檔。 您必須決定要寄送哪些 Dll 和其他檔案。 您也應該閱讀將[Odbc 元件轉散發給您的客戶](../../data/odbc/redistributing-odbc-components-to-your-customers.md)，其中說明如何重新發佈 odbc 元件。

此外，在大部分的情況下，您都必須包含另一個檔案。 Odbccr32 是 ODBC 資料指標程式庫。 此程式庫可為層級1驅動程式提供向前和向後滾動的功能。 它也提供支援快照集的功能。 如需 ODBC 資料指標程式庫的詳細資訊，請參閱[odbc： odbc 資料指標程式庫](../../data/odbc/odbc-the-odbc-cursor-library.md)。

下列主題提供有關搭配使用 ODBC 與資料庫類別的詳細資訊：

- [ODBC：ODBC 資料指標程式庫](../../data/odbc/odbc-the-odbc-cursor-library.md)

- [ODBC：設定 ODBC 資料來源](../../data/odbc/odbc-configuring-an-odbc-data-source.md)

- [ODBC：直接呼叫 ODBC API 函式](../../data/odbc/odbc-calling-odbc-api-functions-directly.md)

## <a name="see-also"></a>另請參閱

[ODBC 基本概念](../../data/odbc/odbc-basics.md)<br/>
[ODBC 管理員](../../data/odbc/odbc-administrator.md)
