---
title: "如何：將 SharePoint 網站設定為私用組件庫 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Sharepoint, 私用組件庫"
  - "私用組件庫, Sharepoint"
ms.assetid: 6c6ed45f-7e46-4ed0-8b5c-839dbbe3769f
caps.latest.revision: 9
caps.handback.revision: 9
manager: "douge"
---
# 如何：將 SharePoint 網站設定為私用組件庫
您可以建立可描述並提供擴充功能作為私用組件庫的 SharePoint 清單頁面，並將清單加入 \[擴充功能和更新\] 中。 如需詳細資訊，請參閱[私用組件庫](../Topic/Private%20Galleries.md)。  
  
 使用 SharePoint 建立私用組件庫  
  
1.  先建立私用組件庫的清單頁面。  
  
2.  然後，將擴充功能 \(.vsix\) 檔案上傳為清單頁面上的項目。  
  
> [!IMPORTANT]
>  基於安全性，SharePoint 會封鎖 .vsix 檔案，不進行上傳。 當您設定私用組件庫時，請確定未封鎖 .vsix 檔案。 如需詳細資訊，請參閱[管理封鎖檔案類型](http://go.microsoft.com/fwlink/?LinkID=201253)。  
  
## 建立私用組件庫的清單頁面  
 根據部署之目標 SharePoint 伺服器的組態，下列步驟可能會不同。 一般而言，這些部署指示也適用於 SharePoint 的任何 WSP 擴充功能。 如需可用於管理 SharePoint 解決方案部署之 STSAdm 工具的說明，請參閱 MSDN Magazine 網站上的[使用 SharePoint 2007 部署解決方案](http://go.microsoft.com/fwlink/?LinkId=220676)。  
  
#### 建立私用組件庫的清單頁面  
  
1.  將 Visual Studio 擴充功能清單 \(.wsp\) 檔案上傳至 SharePoint 伺服器。  
  
2.  在命令提示字元，執行下列命令以在 SharePoint 伺服器上安裝 .wsp 檔案。  
  
     **stsadm –o addsolution –name VisualStudioExtensionsList.wsp**  
  
     **stsadm –o deploysolution –name VisualStudioExtensionsList.wsp –url http:\/\/\<SERVERNAME\> –allowCasPolicies –allowgacdeployment –immediate**  
  
     您也可能需要透過子網站的 SharePoint 使用者介面來啟用這個功能 \(如下所示\)。  
  
    1.  在功能表列上，依序選擇 \[網站動作\]、\[網站設定\] 和 \[管理網站功能\]。  
  
    2.  選擇 \[Visual Studio 擴充程式庫\] 旁邊的 \[啟動\] 按鈕。  
  
    3.  將 Visual Studio 擴充程式庫加入您想要的子網站。  
  
 如果您需要移除清單頁面，請使用下列步驟。  
  
#### 移除私用組件庫的清單頁面  
  
1.  在命令提示字元，執行下列命令以移除 SharePoint 伺服器上的 .wsp 檔案。  
  
     **stsadm –o retractsolution –name VisualStudioExtensionsList.wsp –immediate**  
  
     **stsadm –o deletesolution –name VisualStudioExtensionsList.wsp**  
  
2.  在 SharePoint 中，撤銷並刪除方案。  
  
## 常見問題集  
  
### 上傳擴充功能時，會發生什麼事？  
 上載 Visual Studio 擴充功能 \(.vsix\) 檔案時，會從檔案擷取資訊。 請先從內嵌的 .vsixmanifest 檔案 \(例如 VsixId、VsixVersion 等\) 中擷取一些值，並將其儲存為對應 SPListItem 上的隱藏中繼資料值。 接著，會擷取擴充功能的 Icon 和 PreviewImage 檔案，並將其儲存在個別的清單中。  
  
 影像會儲存在名為 *ListTitle*\_VSIXIcons 和 *ListTitle*\_VSIXPreviewImages 的圖片庫中，其中 *ListTitle* 是可儲存 .vsix 檔案的清單執行個體名稱。 每個影像檔的名稱都會將對應的 VSIX ID 指定為前置詞。  
  
### 刪除擴充功能時，會發生什麼事？  
 刪除 .vsix 檔案時，也會一併刪除對應的影像檔 \(如果有的話\)。  
  
### 更新擴充功能時，會發生什麼事？  
 上傳 .vsix 檔案的新版本並覆寫現有版本，即可更新擴充功能。 更新擴充功能時，會根據新版本中的值來更新擴充功能的所有中繼資料值和影像。  
  
### 刪除清單時，會發生什麼事？  
 刪除 Visual Studio 擴充功能清單的執行個體時，也會一併刪除對應的 \_VSIXIcons 和 \_VSIXPreviewImages 圖片庫。  
  
### 支援的 SharePoint 版本為何？  
 目前，僅支援 SharePoint 2010。  
  
## 請參閱  
 [私用組件庫](../Topic/Private%20Galleries.md)