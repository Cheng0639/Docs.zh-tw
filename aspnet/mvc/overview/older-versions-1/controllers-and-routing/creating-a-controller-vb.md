---
uid: mvc/overview/older-versions-1/controllers-and-routing/creating-a-controller-vb
title: "建立控制站 (VB) |Microsoft 文件"
author: StephenWalther
description: "在本教學課程中，作者： Stephen Walther 會示範如何將控制站新增至 ASP.NET MVC 應用程式。"
ms.author: aspnetcontent
manager: wpickett
ms.date: 03/02/2009
ms.topic: article
ms.assetid: 204b7e86-f560-4611-8adb-785b33e777b9
ms.technology: dotnet-mvc
ms.prod: .net-framework
msc.legacyurl: /mvc/overview/older-versions-1/controllers-and-routing/creating-a-controller-vb
msc.type: authoredcontent
ms.openlocfilehash: d2caf7fe137b48c016ff3cd52db9e36e1e8001c0
ms.sourcegitcommit: 9a9483aceb34591c97451997036a9120c3fe2baf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2017
---
<a name="creating-a-controller-vb"></a><span data-ttu-id="7de94-103">建立控制站 (VB)</span><span class="sxs-lookup"><span data-stu-id="7de94-103">Creating a Controller (VB)</span></span>
====================
<span data-ttu-id="7de94-104">由[Stephen Walther](https://github.com/StephenWalther)</span><span class="sxs-lookup"><span data-stu-id="7de94-104">by [Stephen Walther](https://github.com/StephenWalther)</span></span>

> <span data-ttu-id="7de94-105">在本教學課程中，作者： Stephen Walther 會示範如何將控制站新增至 ASP.NET MVC 應用程式。</span><span class="sxs-lookup"><span data-stu-id="7de94-105">In this tutorial, Stephen Walther demonstrates how you can add a controller to an ASP.NET MVC application.</span></span>


<span data-ttu-id="7de94-106">本教學課程的目標是以說明如何建立新的 ASP.NET MVC 控制站。</span><span class="sxs-lookup"><span data-stu-id="7de94-106">The goal of this tutorial is to explain how you can create new ASP.NET MVC controllers.</span></span> <span data-ttu-id="7de94-107">您了解如何使用 Visual Studio 加入控制器 功能表選項，藉由建立類別檔案，以手動方式建立控制站。</span><span class="sxs-lookup"><span data-stu-id="7de94-107">You learn how to create controllers both by using the Visual Studio Add Controller menu option and by creating a class file by hand.</span></span>

### <a name="using-the-add-controller-menu-option"></a><span data-ttu-id="7de94-108">使用新增控制器功能表選項</span><span class="sxs-lookup"><span data-stu-id="7de94-108">Using the Add Controller Menu Option</span></span>

<span data-ttu-id="7de94-109">若要建立新的控制站最簡單方式是在 Visual Studio 方案總管 視窗中的 控制器 資料夾上按一下滑鼠右鍵，然後選取**新增、 控制站**功能表選項 （請參閱圖 1）。</span><span class="sxs-lookup"><span data-stu-id="7de94-109">The easiest way to create a new controller is to right-click the Controllers folder in the Visual Studio Solution Explorer window and select the **Add, Controller** menu option (see Figure 1).</span></span> <span data-ttu-id="7de94-110">選取此功能表選項會開啟**加入控制器**對話方塊 （請參閱圖 2）。</span><span class="sxs-lookup"><span data-stu-id="7de94-110">Selecting this menu option opens the **Add Controller** dialog (see Figure 2).</span></span>


<span data-ttu-id="7de94-111">[![新增專案 對話方塊](creating-a-controller-vb/_static/image1.jpg)](creating-a-controller-vb/_static/image1.png)</span><span class="sxs-lookup"><span data-stu-id="7de94-111">[![The New Project dialog box](creating-a-controller-vb/_static/image1.jpg)](creating-a-controller-vb/_static/image1.png)</span></span>

<span data-ttu-id="7de94-112">**圖 01**： 加入新的控制站 ([按一下以檢視完整大小的影像](creating-a-controller-vb/_static/image2.png))</span><span class="sxs-lookup"><span data-stu-id="7de94-112">**Figure 01**: Adding a new controller([Click to view full-size image](creating-a-controller-vb/_static/image2.png))</span></span>


<span data-ttu-id="7de94-113">[![新增專案 對話方塊](creating-a-controller-vb/_static/image2.jpg)](creating-a-controller-vb/_static/image3.png)</span><span class="sxs-lookup"><span data-stu-id="7de94-113">[![The New Project dialog box](creating-a-controller-vb/_static/image2.jpg)](creating-a-controller-vb/_static/image3.png)</span></span>

<span data-ttu-id="7de94-114">**圖 02**: 加入控制器 對話方塊 ([按一下以檢視完整大小的影像](creating-a-controller-vb/_static/image4.png))</span><span class="sxs-lookup"><span data-stu-id="7de94-114">**Figure 02**: The Add Controller dialog ([Click to view full-size image](creating-a-controller-vb/_static/image4.png))</span></span>


<span data-ttu-id="7de94-115">請注意，控制器名稱的第一個部分會反白顯示**加入控制器**對話方塊。</span><span class="sxs-lookup"><span data-stu-id="7de94-115">Notice that the first part of the controller name is highlighted in the **Add Controller** dialog.</span></span> <span data-ttu-id="7de94-116">每個控制站名稱必須以後置字元結尾*控制器*。</span><span class="sxs-lookup"><span data-stu-id="7de94-116">Every controller name must end with the suffix *Controller*.</span></span> <span data-ttu-id="7de94-117">例如，您可以在其中建立名為控制器*ProductController*但不是將名為控制器*產品*。</span><span class="sxs-lookup"><span data-stu-id="7de94-117">For example, you can create a controller named *ProductController* but not a controller named *Product*.</span></span>


<span data-ttu-id="7de94-118">如果您建立遺漏的控制站*控制器*後置詞，則您將無法叫用控制器。</span><span class="sxs-lookup"><span data-stu-id="7de94-118">If you create a controller that is missing the *Controller* suffix then you won't be able to invoke the controller.</span></span> <span data-ttu-id="7de94-119">不要執行這個動作--我所浪費我生命週期的無數小時後進行這種錯誤。</span><span class="sxs-lookup"><span data-stu-id="7de94-119">Don't do this -- I've wasted countless hours of my life after making this mistake.</span></span>


<span data-ttu-id="7de94-120">**列出 1-Controllers\ProductController.vb**</span><span class="sxs-lookup"><span data-stu-id="7de94-120">**Listing 1 - Controllers\ProductController.vb**</span></span>

[!code-vb[Main](creating-a-controller-vb/samples/sample1.vb)]

<span data-ttu-id="7de94-121">在 [控制器] 資料夾中，您應該一律建立控制器。</span><span class="sxs-lookup"><span data-stu-id="7de94-121">You should always create controllers in the Controllers folder.</span></span> <span data-ttu-id="7de94-122">否則，會違反您的 ASP.NET MVC 的慣例，其他開發人員必須了解您的應用程式更難。</span><span class="sxs-lookup"><span data-stu-id="7de94-122">Otherwise, you'll be violating the conventions of ASP.NET MVC and other developers will have a more difficult time understanding your application.</span></span>

### <a name="scaffolding-action-methods"></a><span data-ttu-id="7de94-123">Scaffolding 動作方法</span><span class="sxs-lookup"><span data-stu-id="7de94-123">Scaffolding Action Methods</span></span>

<span data-ttu-id="7de94-124">當您建立一個控制站時，您可以選擇自動產生建立、 更新和詳細資料的動作方法 （請參閱圖 3）。</span><span class="sxs-lookup"><span data-stu-id="7de94-124">When you create a controller, you have the option to generate Create, Update, and Details action methods automatically (see Figure 3).</span></span> <span data-ttu-id="7de94-125">如果您選取此選項會產生清單 2 控制器類別。</span><span class="sxs-lookup"><span data-stu-id="7de94-125">If you select this option then the controller class in Listing 2 is generated.</span></span>


<span data-ttu-id="7de94-126">[![自動建立動作方法](creating-a-controller-vb/_static/image3.jpg)](creating-a-controller-vb/_static/image5.png)</span><span class="sxs-lookup"><span data-stu-id="7de94-126">[![Creating action methods automatically](creating-a-controller-vb/_static/image3.jpg)](creating-a-controller-vb/_static/image5.png)</span></span>

<span data-ttu-id="7de94-127">**圖 03**： 建立動作方法會自動 ([按一下以檢視完整大小的影像](creating-a-controller-vb/_static/image6.png))</span><span class="sxs-lookup"><span data-stu-id="7de94-127">**Figure 03**: Creating action methods automatically ([Click to view full-size image](creating-a-controller-vb/_static/image6.png))</span></span>


<span data-ttu-id="7de94-128">**列出 2-Controllers\CustomerController.vb**</span><span class="sxs-lookup"><span data-stu-id="7de94-128">**Listing 2 - Controllers\CustomerController.vb**</span></span>

[!code-vb[Main](creating-a-controller-vb/samples/sample2.vb)]

<span data-ttu-id="7de94-129">這些產生的方法都是虛設常式方法。</span><span class="sxs-lookup"><span data-stu-id="7de94-129">These generated methods are stub methods.</span></span> <span data-ttu-id="7de94-130">您必須將建立、 更新和顯示詳細資料的客戶自己的實際邏輯。</span><span class="sxs-lookup"><span data-stu-id="7de94-130">You must add the actual logic for creating, updating, and showing details for a customer yourself.</span></span> <span data-ttu-id="7de94-131">但是，虛設常式方法會將您提供不錯的起點。</span><span class="sxs-lookup"><span data-stu-id="7de94-131">But, the stub methods provide you with a nice starting point.</span></span>

### <a name="creating-a-controller-class"></a><span data-ttu-id="7de94-132">建立控制器類別</span><span class="sxs-lookup"><span data-stu-id="7de94-132">Creating a Controller Class</span></span>

<span data-ttu-id="7de94-133">ASP.NET MVC 控制器是只在類別。</span><span class="sxs-lookup"><span data-stu-id="7de94-133">The ASP.NET MVC controller is just a class.</span></span> <span data-ttu-id="7de94-134">如果您想要的話，您可以略過方便的 Visual Studio 控制器 scaffolding，並以手動方式建立控制器類別。</span><span class="sxs-lookup"><span data-stu-id="7de94-134">If you prefer, you can ignore the convenient Visual Studio controller scaffolding and create a controller class by hand.</span></span> <span data-ttu-id="7de94-135">請依照下列步驟：</span><span class="sxs-lookup"><span data-stu-id="7de94-135">Follow these steps:</span></span>

1. <span data-ttu-id="7de94-136">以滑鼠右鍵按一下 [控制器] 資料夾，然後選取功能表選項**新增]、 [新項目**選取**類別**範本 （請參閱圖 4）。</span><span class="sxs-lookup"><span data-stu-id="7de94-136">Right-click the Controllers folder and select the menu option **Add, New Item** and select the **Class** template (see Figure 4).</span></span>
2. <span data-ttu-id="7de94-137">將新類別 PersonController.vb，然後按一下**新增** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="7de94-137">Name the new class PersonController.vb and click the **Add** button.</span></span>
3. <span data-ttu-id="7de94-138">修改產生的類別檔案，使該類別繼承自基底 System.Web.Mvc.Controller 類別 （請參閱列出 3）。</span><span class="sxs-lookup"><span data-stu-id="7de94-138">Modify the resulting class file so that the class inherits from the base System.Web.Mvc.Controller class (see Listing 3).</span></span>


<span data-ttu-id="7de94-139">[![建立新的類別](creating-a-controller-vb/_static/image4.jpg)](creating-a-controller-vb/_static/image7.png)</span><span class="sxs-lookup"><span data-stu-id="7de94-139">[![Creating a new class](creating-a-controller-vb/_static/image4.jpg)](creating-a-controller-vb/_static/image7.png)</span></span>

<span data-ttu-id="7de94-140">**圖 04**： 建立新的類別 ([按一下以檢視完整大小的影像](creating-a-controller-vb/_static/image8.png))</span><span class="sxs-lookup"><span data-stu-id="7de94-140">**Figure 04**: Creating a new class([Click to view full-size image](creating-a-controller-vb/_static/image8.png))</span></span>


<span data-ttu-id="7de94-141">**列出 3-Controllers\PersonController.vb**</span><span class="sxs-lookup"><span data-stu-id="7de94-141">**Listing 3 - Controllers\PersonController.vb**</span></span>

[!code-vb[Main](creating-a-controller-vb/samples/sample3.vb)]

<span data-ttu-id="7de94-142">列出的 3 中的控制站會公開一個名為 index （） 會傳回字串"Hello World ！"的動作。</span><span class="sxs-lookup"><span data-stu-id="7de94-142">The controller in Listing 3 exposes one action named Index() that returns the string "Hello World!".</span></span> <span data-ttu-id="7de94-143">您可以叫用此控制器動作，以執行您的應用程式，並要求的 URL 如下所示：</span><span class="sxs-lookup"><span data-stu-id="7de94-143">You can invoke this controller action by running your application and requesting a URL like the following:</span></span>

`http://localhost:40071/Person`

> [!NOTE] 
> 
> <span data-ttu-id="7de94-144">ASP.NET 程式開發伺服器會使用隨機的連接埠號碼 (例如，40071)。</span><span class="sxs-lookup"><span data-stu-id="7de94-144">The ASP.NET Development Server uses a random port number (for example, 40071).</span></span> <span data-ttu-id="7de94-145">輸入時要叫用控制器的 URL，您必須提供正確的連接埠號碼。</span><span class="sxs-lookup"><span data-stu-id="7de94-145">When entering a URL to invoke a controller, you'll need to supply the right port number.</span></span> <span data-ttu-id="7de94-146">ASP.NET 程式開發伺服器，Windows 通知區域 （右下方的螢幕） 中將滑鼠停留在圖示，您可以判斷通訊埠編號。</span><span class="sxs-lookup"><span data-stu-id="7de94-146">You can determine the port number by hovering your mouse over the icon for the ASP.NET Development Server in the Windows Notification Area (bottom-right of your screen).</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="7de94-147">[上一頁](adding-dynamic-content-to-a-cached-page-vb.md)
[下一頁](creating-an-action-vb.md)</span><span class="sxs-lookup"><span data-stu-id="7de94-147">[Previous](adding-dynamic-content-to-a-cached-page-vb.md)
[Next](creating-an-action-vb.md)</span></span>