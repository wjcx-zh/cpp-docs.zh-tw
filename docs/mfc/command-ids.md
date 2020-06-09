---
title: 命令 ID
ms.date: 11/04/2016
helpviewer_keywords:
- command IDs, MFC
- command IDs
ms.assetid: e0171a2b-45b9-41fa-945d-ec2f7602ded0
ms.openlocfilehash: f7d675891904301b16aafe3acb2c294eede6d8d8
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619044"
---
# <a name="command-ids"></a>命令 ID

命令會由單獨的命令識別碼（在**WM_COMMAND**訊息中編碼）完整描述。 這個識別碼會指派給產生命令的使用者介面物件。 一般而言，識別碼會針對其所指派之使用者介面物件的功能進行命名。

例如，[編輯] 功能表中的 [全部清除] 專案可能會被指派一個識別碼，例如**ID_EDIT_CLEAR_ALL**。 類別庫會預先定義一些識別碼，特別是架構處理本身的命令，例如**ID_EDIT_CLEAR_ALL**或**ID_FILE_OPEN**。 您將自行建立其他命令識別碼。

當您在 [Visual C++ 功能表編輯器] 中建立自己的功能表時，最好遵循類別庫的命名慣例，如**ID_FILE_OPEN**所述。 [標準命令](standard-commands.md)會說明類別庫所定義的標準命令。

## <a name="see-also"></a>另請參閱

[使用者介面物件和命令識別碼](user-interface-objects-and-command-ids.md)
