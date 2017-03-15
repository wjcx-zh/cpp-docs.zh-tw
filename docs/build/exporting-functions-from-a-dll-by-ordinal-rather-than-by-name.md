---
title: "根據序數而不是名稱從 DLL 匯出函式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "NONAME"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "匯出 DLL [C++], 序數值"
  - "匯出函式 [C++], 序數值"
  - "NONAME 屬性"
  - "序數匯出 [C++]"
ms.assetid: 679719fd-d965-4df3-9f7a-7d86ad831702
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 根據序數而不是名稱從 DLL 匯出函式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

從您的 DLL 匯出函式最簡單的方法是以名稱匯出。  例如，當您使用 **\_\_declspec\(dllexport\)** 時就會以這種方式匯出。  但是您可以序數匯出函式來取代。  使用這項技巧時，您必須使用 .def 檔而不是 **\_\_declspec\(dllexport\)**。  若要指定函式的序數值，請將它的序數附加到 .def 檔中的函式名稱。  如需指定序數的詳細資訊，請參閱[使用 .def 檔從 DLL 匯出](../build/exporting-from-a-dll-using-def-files.md)。  
  
> [!TIP]
>  如果您要最佳化 DLL 檔案大小，請在每個匯出的函式上使用 **NONAME** 屬性 \(Attribute\)。  使用 **NONAME** 屬性，儲存在 DLL 的匯出表的將會是序數而不是函式名稱。  這種方式可以在匯出許多函式時省下許多步驟。  
  
## 您想要執行甚麼工作？  
  
-   [使用 .def 檔，這樣我可以依序數匯出](../build/exporting-from-a-dll-using-def-files.md)  
  
-   [使用 \_\_declspec\(dllexport\)](../build/exporting-from-a-dll-using-declspec-dllexport.md)  
  
## 請參閱  
 [從 DLL 匯出](../build/exporting-from-a-dll.md)