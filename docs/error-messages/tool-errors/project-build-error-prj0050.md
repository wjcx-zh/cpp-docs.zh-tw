---
title: "專案建置錯誤 PRJ0050 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- PRJ0050
dev_langs:
- C++
helpviewer_keywords:
- PRJ0050
ms.assetid: ceef3b37-0acf-4abd-ac62-aa830b4fa145
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e9d9b123da2e32db0f695c31bc9643a481d352b8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="project-build-error-prj0050"></a>專案建置錯誤 PRJ0050
無法註冊輸出。 請確定您有適當的權限可以修改登錄。  
  
 Visual c + + 建置系統無法註冊組建 （dll 或.exe） 的輸出。 您必須修改登錄的系統管理員身分登入。  
  
 如果您建立.dll，您可以嘗試登錄以手動方式使用 regsvr32.exe 此.dll 檔，這應會顯示組建失敗的原因的相關資訊。  
  
 如果您不建立.dll，查看組建記錄檔，會造成錯誤的命令。