---
title: "專案建置錯誤 PRJ0030 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: PRJ0030
dev_langs: C++
helpviewer_keywords: PRJ0030
ms.assetid: c48b3727-e166-46e7-bcd7-3e5b2ac5c1d4
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b6fe537dd8e6705fd5e30929a2480eb1d9ef9119
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="project-build-error-prj0030"></a>專案建置錯誤 PRJ0030
巨集展開發生錯誤。 評估遞迴超過 32 個層級為 $（巨集）。  
  
 這個錯誤被因您在巨集中的遞迴。 例如，如果您設定**中繼目錄**屬性 (請參閱[一般屬性頁 （專案）](../../ide/general-property-page-project.md)) (IntDir)，您會有遞迴。  
  
 若要解決這個錯誤，不會定義巨集或根據它們用來定義的巨集的屬性。