---
title: "/DLL (建置 DLL) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/dll"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/DLL 連結器選項 [C++]"
  - "-DLL 連結器選項"
  - "DLL 連結器選項 [C++]"
  - "DLL [C++], 建置"
  - "匯出 DLL [C++], 指定匯出"
ms.assetid: c7685aec-31d0-490f-9503-fb5171a23609
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /DLL (建置 DLL)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/DLL  
```  
  
## 備註  
 \/DLL 選項會建置一個 DLL 做為主要輸出檔。  DLL 通常含有可以被其他程式使用的匯出。  有三種方法可指定匯出，依建議使用順序列出：  
  
1.  在原始程式碼中的 [\_\_declspec\(dllexport\)](../../cpp/dllexport-dllimport.md)  
  
2.  .def 檔中的 [EXPORTS](../../build/reference/exports.md) 陳述式  
  
3.  LINK 命令中的 [\/EXPORT](../../build/reference/export-exports-a-function.md) 規格  
  
 一個程式中可以使用一種以上的方法。  
  
 另一種建置 DLL 的方法是使用 **LIBRARY** 模組定義陳述式。  \/BASE 和 \/DLL 選項合在一起就相當於 **LIBRARY** 陳述式。  
  
 請不要在開發環境中指定這個選項；這個選項只能使用於命令列上。  這個選項是當您使用應用程式精靈建立 DLL 專案時設定的。  
  
 請注意，如果您在建立 .dll 之前的預備步驟中，建立匯入程式庫，則在建置 .dll 時，必須傳遞於建置匯入程式庫時所用的同一組物件檔。  
  
### 若要在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱[設定 Visual C\+\+ 專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  按一下 \[組態屬性\] 資料夾。  
  
3.  按一下 \[一般\] 屬性頁。  
  
4.  修改 \[組態型別\] 屬性。  
  
### 若要以程式設計方式設定這個連結器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCPropertySheet.ConfigurationType%2A>。  
  
## 請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)