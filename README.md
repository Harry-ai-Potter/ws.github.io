<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>旅途无忧 - 您的专业旅游服务平台</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: "Microsoft YaHei", sans-serif;
        }
        body {
            background-color: #f9f9f9;
            color: #333;
        }
        .container {
            width: 1200px;
            margin: 0 auto;
            padding: 20px 0;
        }
        /* 顶部导航栏 */
        .top-bar {
            background-color: #fff;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
            padding: 10px 0;
            position: sticky;
            top: 0;
            z-index: 100;
        }
        .nav-container {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        .logo {
            font-size: 24px;
            font-weight: bold;
            color: #0066cc;
        }
        .logo span {
            color: #ff6600;
        }
        .nav-menu {
            display: flex;
            list-style: none;
        }
        .nav-menu li {
            margin-left: 20px;
        }
        .nav-menu a {
            text-decoration: none;
            color: #333;
            font-weight: 500;
            transition: color 0.3s;
        }
        .nav-menu a:hover {
            color: #0066cc;
        }
        .user-actions a {
            text-decoration: none;
            color: #666;
            margin-left: 15px;
            font-size: 14px;
        }
        .user-actions a:hover {
            color: #0066cc;
        }
        /* 搜索空间栏 */
        .search-bar {
            background-color: #f0f8ff;
            padding: 20px 0;
            margin-bottom: 30px;
            border-radius: 8px;
        }
        .search-container {
            display: flex;
            max-width: 700px;
            margin: 0 auto;
        }
        .search-input {
            flex: 1;
            padding: 12px 15px;
            border: 2px solid #0066cc;
            border-right: none;
            border-radius: 4px 0 0 4px;
            font-size: 16px;
            outline: none;
        }
        .search-button {
            background-color: #0066cc;
            color: white;
            border: none;
            padding: 0 25px;
            border-radius: 0 4px 4px 0;
            cursor: pointer;
            font-size: 16px;
            font-weight: bold;
        }
        /* 主要内容区 */
        .main-content {
            display: grid;
            grid-template-columns: 200px 1fr;
            gap: 30px;
        }
        /* 左侧栏 */
        .sidebar {
            background-color: #fff;
            border-radius: 8px;
            padding: 20px;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.05);
        }
        .sidebar-title {
            font-size: 18px;
            margin-bottom: 15px;
            padding-bottom: 10px;
            border-bottom: 1px solid #eee;
            color: #0066cc;
        }
        .sidebar-menu {
            list-style: none;
        }
        .sidebar-menu li {
            margin-bottom: 12px;
        }
        .sidebar-menu a {
            text-decoration: none;
            color: #555;
            display: block;
            padding: 8px 10px;
            border-radius: 4px;
            transition: all 0.3s;
        }
        .sidebar-menu a:hover {
            background-color: #f0f8ff;
            color: #0066cc;
            padding-left: 15px;
        }
        /* 右侧内容区 */
        .content {
            display: flex;
            flex-direction: column;
            gap: 30px;
        }
        .section {
            background-color: #fff;
            border-radius: 8px;
            padding: 25px;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.05);
        }
        .section-title {
            font-size: 22px;
            margin-bottom: 20px;
            color: #0066cc;
            display: flex;
            align-items: center;
        }
        .section-title::after {
            content: "";
            flex: 1;
            height: 1px;
            background-color: #eee;
            margin-left: 15px;
        }
        /* 热门目的地 */
        .destinations-grid {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 20px;
        }
        .destination-card {
            border-radius: 8px;
            overflow: hidden;
            box-shadow: 0 3px 10px rgba(0, 0, 0, 0.1);
            transition: transform 0.3s;
        }
        .destination-card:hover {
            transform: translateY(-5px);
        }
        .destination-img {
            height: 180px;
            overflow: hidden;
        }
        .destination-img img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            transition: transform 0.5s;
        }
        .destination-card:hover .destination-img img {
            transform: scale(1.05);
        }
        .destination-info {
            padding: 15px;
        }
        .destination-name {
            font-size: 18px;
            margin-bottom: 8px;
            color: #333;
        }
        .destination-desc {
            font-size: 14px;
            color: #666;
            margin-bottom: 10px;
            height: 40px;
            overflow: hidden;
        }
        .destination-price {
            color: #ff6600;
            font-weight: bold;
            font-size: 18px;
        }
        .destination-price small {
            font-size: 14px;
            color: #999;
            text-decoration: line-through;
            margin-left: 5px;
        }
        /* 旅游攻略 */
        .guides-list {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 20px;
        }
        .guide-card {
            display: flex;
            background-color: #f9f9f9;
            border-radius: 8px;
            overflow: hidden;
        }
        .guide-img {
            width: 120px;
            height: 120px;
            flex-shrink: 0;
        }
        .guide-img img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }
        .guide-content {
            padding: 12px;
            flex: 1;
        }
        .guide-title {
            font-size: 16px;
            margin-bottom: 8px;
            color: #333;
        }
        .guide-excerpt {
            font-size: 13px;
            color: #666;
            margin-bottom: 10px;
            display: -webkit-box;
            -webkit-line-clamp: 2;
            -webkit-box-orient: vertical;
            overflow: hidden;
        }
        .guide-meta {
            display: flex;
            justify-content: space-between;
            font-size: 12px;
            color: #999;
        }
        /* 旅游线路 */
        .tours-grid {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 25px;
        }
        .tour-card {
            background-color: #fff;
            border-radius: 8px;
            overflow: hidden;
            box-shadow: 0 3px 10px rgba(0, 0, 0, 0.1);
        }
        .tour-img {
            height: 160px;
            position: relative;
        }
        .tour-img img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }
        .tour-badge {
            position: absolute;
            top: 10px;
            right: 10px;
            background-color: #ff6600;
            color: white;
            padding: 4px 8px;
            border-radius: 4px;
            font-size: 12px;
        }
        .tour-info {
            padding: 18px;
        }
        .tour-title {
            font-size: 18px;
            margin-bottom: 10px;
            color: #333;
        }
        .tour-meta {
            display: flex;
            justify-content: space-between;
            margin-bottom: 15px;
            font-size: 14px;
            color: #666;
        }
        .tour-price {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        .tour-price-value {
            color: #ff6600;
            font-size: 22px;
            font-weight: bold;
        }
        .tour-price-value small {
            font-size: 14px;
            color: #999;
            text-decoration: line-through;
            margin-left: 5px;
        }
        .tour-button {
            background-color: #0066cc;
            color: white;
            border: none;
            padding: 6px 15px;
            border-radius: 4px;
            cursor: pointer;
            font-size: 14px;
            transition: background-color 0.3s;
        }
        .tour-button:hover {
            background-color: #0055aa;
        }
        /* 页脚 */
        .footer {
            background-color: #333;
            color: #ccc;
            padding: 40px 0 20px;
            margin-top: 50px;
        }
        .footer-container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 15px;
        }
        .footer-content {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 30px;
            margin-bottom: 30px;
        }
        .footer-column h3 {
            color: #fff;
            margin-bottom: 20px;
            font-size: 18px;
        }
        .footer-links {
            list-style: none;
        }
        .footer-links li {
            margin-bottom: 10px;
        }
        .footer-links a {
            color: #ccc;
            text-decoration: none;
            font-size: 14px;
            transition: color 0.3s;
        }
        .footer-links a:hover {
            color: #fff;
        }
        .footer-bottom {
            text-align: center;
            padding-top: 20px;
            border-top: 1px solid #444;
            font-size: 14px;
        }
    </style>
</head>
<body>
    <!-- 顶部导航栏 -->
    <div class="top-bar">
        <div class="container nav-container">
            <div class="logo">旅途<span>无忧</span></div>
            <ul class="nav-menu">
                <li><a href="#">首页</a></li>
                <li><a href="#">目的地</a></li>
                <li><a href="#">旅游线路</a></li>
                <li><a href="#">旅游攻略</a></li>
                <li><a href="#">特色活动</a></li>
                <li><a href="#">关于我们</a></li>
            </ul>
            <div class="user-actions">
                <a href="#">登录</a>
                <a href="#">注册</a>
                <a href="#">我的订单</a>
                <a href="#">购物车</a>
            </div>
        </div>
    </div>
    <!-- 主要内容区 -->
    <div class="container">
        <!-- 搜索功能栏 -->
        <div class="search-bar">
            <div class="search-container">
                <input type="text" class="search-input" placeholder="搜索目的地、景点、旅游线路...">
                <button class="search-button">搜索</button>
            </div>
        </div>
        <!-- 主要内容区 -->
        <div class="main-content">
            <!-- 左侧栏 -->
            <div class="sidebar">
                <h3 class="sidebar-title">旅游分类</h3>
                <ul class="sidebar-menu">
                    <li><a href="#">境内游</a></li>
                    <li><a href="#">境外游</a></li>
                    <li><a href="#">跟团游</a></li>
                    <li><a href="#">自由行</a></li>
                    <li><a href="#">邮轮游</a></li>
                    <li><a href="#">亲子游</a></li>
                    <li><a href="#">情侣游</a></li>
                    <li><a href="#">商务游</a></li>
                    <li><a href="#">定制游</a></li>
                    <li><a href="#">蜜月游</a></li>
                </ul>
                <h3 class="sidebar-title" style="margin-top: 30px;">热门景点</h3>
                <ul class="sidebar-menu">
                    <li><a href="#">三亚</a></li>
                    <li><a href="#">丽江</a></li>
                    <li><a href="#">张家界</a></li>
                    <li><a href="#">西藏</a></li>
                    <li><a href="#">厦门</a></li>
                    <li><a href="#">北京</a></li>
                    <li><a href="#">上海</a></li>
                    <li><a href="#">成都</a></li>
                    <li><a href="#">西安</a></li>
                    <li><a href="#">杭州</a></li>
                </ul>
            </div>
            <!-- 右侧内容区 -->
            <div class="content">
                <!-- 项目概述 -->
                <div class="section">
                    <h2 class="section-title">项目概述</h2>
                    <p>旅途无忧是一个专业的旅游服务平台，致力于为用户提供丰富多样的旅游产品和优质的服务体验。我们提供境内外旅游线路、自由行套餐、酒店预订、机票预订等一站式旅游服务。</p>
                    <p>我们的目标是让每一次旅行都成为难忘的美好回忆，让每一位游客都能体验到不同地方的风土人情和独特魅力。通过与众多优质供应商合作，我们精心打造每一个旅游产品，确保行程安排合理、住宿舒适、餐饮特色，带给您无忧无虑的旅行体验。</p>
                </div>
                <!-- 商业分析 -->
                <div class="section">
                    <h2 class="section-title">商业分析</h2>
                    <!-- 价值服务 -->
                    <h3 style="margin-bottom: 15px; color: #333;">价值服务</h3>
                    <p>我们提供的旅游服务包括精心策划的旅游线路、专业贴心的导游服务、品质保障的酒店住宿、安全便捷的交通安排等。无论是跟团游还是自由行，我们都能满足不同游客的需求，提供个性化的旅游解决方案。</p>
                    <!-- 关键服务 -->
                    <h3 style="margin-bottom: 15px; color: #333; margin-top: 20px;">关键服务</h3>
                    <p>我们的关键服务在于专业的旅游规划和行程安排。我们拥有一支经验丰富的旅游顾问团队，他们熟悉各地旅游资源和游客需求，能够根据游客的喜好和预算，设计出最适合的旅游线路。同时，我们与众多优质供应商建立了长期合作关系，确保旅游产品的品质和服务质量。</p>
                    <!-- 核心资源 -->
                    <h3 style="margin-bottom: 15px; color: #333; margin-top: 20px;">核心资源</h3>
                    <p>我们的核心资源包括专业的旅游顾问团队、丰富的旅游资源网络、先进的旅游管理系统、良好的品牌口碑等。这些资源是我们提供优质旅游服务的基础，也是我们在旅游市场中脱颖而出的重要保障。</p>
                    <!-- 客户群体 -->
                    <h3 style="margin-bottom: 15px; color: #333; margin-top: 20px;">客户群体</h3>
                    <p>我们的目标客户群体广泛，包括家庭游客、情侣、朋友、商务人士、老年人、年轻人等。无论是休闲度假、亲子出行、蜜月旅行还是商务考察，我们都能提供相应的旅游产品和服务，满足不同客户群体的需求。</p>
                    <!-- 客户关系 -->
                    <h3 style="margin-bottom: 15px; color: #333; margin-top: 20px;">客户关系</h3>
                    <p>我们注重与客户的沟通和互动，通过专业的旅游顾问提供一对一咨询服务，及时解答客户的疑问和需求。在旅行过程中，我们的导游和地接人员会全程陪伴，确保客户的旅行体验。旅行结束后，我们还会通过回访和调查收集客户的反馈，不断改进我们的服务。</p>
                    <!-- 渠道通道 -->
                    <h3 style="margin-bottom: 15px; color: #333; margin-top: 20px;">渠道通道</h3>
                    <p>我们的销售渠道包括官方网站、移动应用、社交媒体平台、线下门店等。我们通过多种渠道进行宣传和推广，提高品牌知名度和产品曝光度。同时，我们与各大旅游平台合作，拓宽销售渠道，方便客户预订旅游产品。</p>
                    <!-- 重要合作 -->
                    <h3 style="margin-bottom: 15px; color: #333; margin-top: 20px;">重要合作</h3>
                    <p>我们与众多航空公司、酒店集团、景区景点、地接社等建立了长期稳定的合作关系。通过与优质供应商的合作，我们能够为客户提供更具竞争力的价格和更优质的旅游产品。同时，我们也积极与旅游相关机构和组织合作，共同推动旅游行业的发展。</p>
                    <!-- 成本结构 -->
                    <h3 style="margin-bottom: 15px; color: #333; margin-top: 20px;">成本结构</h3>
                    <p>我们的成本主要包括产品研发成本、市场推广成本、运营成本、人力成本等。我们通过优化运营流程、提高效率、控制成本等方式，在保证服务质量的前提下，降低运营成本，提高盈利能力。</p>
                    <!-- 收入来源 -->
                    <h3 style="margin-bottom: 15px; color: #333; margin-top: 20px;">收入来源</h3>
                    <p>我们的收入主要来源于旅游产品销售、服务收费、广告合作等。随着业务的不断拓展和客户群体的扩大，我们的收入也在稳步增长。我们致力于通过多元化的产品和服务，增加收入来源，提高盈利水平。</p>
                </div>
                <!-- 热门目的地 -->
                <div class="section">
                    <h2 class="section-title">热门目的地</h2>
                    <div class="destinations-grid">
                        <div class="destination-card">
                            <div class="destination-img">
                                <img src="https://images.unsplash.com/photo-1548919973-5cef591cdbc9?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1000&q=80" alt="三亚">
                            </div>
                            <div class="destination-info">
                                <h3 class="destination-name">三亚</h3>
                                <p class="destination-desc">阳光沙滩，热带风情，尽享海岛度假的惬意时光</p>
                                <div class="destination-price">¥2,999 <small>起</small></div>
                            </div>
                        </div>
                        <div class="destination-card">
                            <div class="destination-img">
                                <img src="https://images.unsplash.com/photo-1508804185872-d7badad00f7d?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1000&q=80" alt="丽江">
                            </div>
                            <div class="destination-info">
                                <h3 class="destination-name">丽江</h3>
                                <p class="destination-desc">古城风情，雪山美景，感受纳西族的独特文化</p>
                                <div class="destination-price">¥1,899 <small>起</small></div>
                            </div>
                        </div>
                        <div class="destination-card">
                            <div class="destination-img">
                                <img src="https://images.unsplash.com/photo-1464822759023-fed622ff2c3b?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1000&q=80" alt="西藏">
                            </div>
                            <div class="destination-info">
                                <h3 class="destination-name">西藏</h3>
                                <p class="destination-desc">雪域高原，神圣寺庙，体验心灵的洗礼之旅</p>
                                <div class="destination-price">¥5,999 <small>起</small></div>
                            </div>
                        </div>
                    </div>
                </div>
                <!-- 旅游攻略 -->
                <div class="section">
                    <h2 class="section-title">旅游攻略</h2>
                    <div class="guides-list">
                        <div class="guide-card">
                            <div class="guide-img">
                                <img src="https://images.unsplash.com/photo-1502602898657-3e91760cbb34?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=500&q=80" alt="旅行摄影攻略">
                            </div>
                            <div class="guide-content">
                                <h3 class="guide-title">旅行摄影攻略：如何拍出专业级风景照片</h3>
                                <p class="guide-excerpt">掌握这些摄影技巧，让你的旅行照片不再平凡，轻松拍出令人惊叹的风景大片。</p>
                                <div class="guide-meta">
                                    <span>2024-06-15</span>
                                    <span>阅读量：2,345</span>
                                </div>
                            </div>
                        </div>
                        <div class="guide-card">
                            <div class="guide-img">
                                <img src="https://images.unsplash.com/photo-1476224203421-9ac39bcb3327?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=500&q=80" alt="美食攻略">
                            </div>
                            <div class="guide-content">
                                <h3 class="guide-title">各地美食攻略：品尝当地特色美食的绝佳去处</h3>
                                <p class="guide-excerpt">旅行不止是看风景，还有品尝美食。这份攻略带你找到各地最地道的美食餐厅。</p>
                                <div class="guide-meta">
                                    <span>2024-06-10</span>
                                    <span>阅读量：3,127</span>
                                </div>
                            </div>
                        </div>
                        <div class="guide-card">
                            <div class="guide-img">
                                <img src="https://images.unsplash.com/photo-1501555088652-021faa106b9b?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=500&q=80" alt="行前准备">
                            </div>
                            <div class="guide-content">
                                <h3 class="guide-title">行前准备攻略：让你的旅行更加轻松愉快</h3>
                                <p class="guide-excerpt">从证件办理到行李打包，从行程规划到预算控制，这份攻略帮你做好一切行前准备。</p>
                                <div class="guide-meta">
                                    <span>2024-06-05</span>
                                    <span>阅读量：4,568</span>
                                </div>
                            </div>
                        </div>
                        <div class="guide-card">
                            <div class="guide-img">
                                <img src="https://images.unsplash.com/photo-1439853949127-fa647821eba0?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=500&q=80" alt="旅行住宿">
                            </div>
                            <div class="guide-content">
                                <h3 class="guide-title">旅行住宿攻略：如何选择最适合的住宿</h3>
                                <p class="guide-excerpt">从星级酒店到特色民宿，从经济实惠到豪华享受，这份攻略帮你找到理想的住宿。</p>
                                <div class="guide-meta">
                                    <span>2024-05-28</span>
                                    <span>阅读量：2,890</span>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
                <!-- 旅游线路 -->
                <div class="section">
                    <h2 class="section-title">热门旅游线路</h2>
                    <div class="tours-grid">
                        <div class="tour-card">
                            <div class="tour-img">
                                <img src="https://images.unsplash.com/photo-1520250497591-112fobf10429?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1000&q=80" alt="云南大理丽江六日游">
                                <div class="tour-badge">热门</div>
                            </div>
                            <div class="tour-info">
                                <h3 class="tour-title">云南大理丽江六日游</h3>
                                <div class="tour-meta">
                                    <span>6天5晚</span>
                                    <span>跟团游</span>
                                </div>
                                <div class="tour-price">
                                    <div>
                                        <div class="tour-price-value">¥3,299 <small>¥3,999</small></div>
                                        <span style="font-size: 14px; color: #666;">已售1,234</span>
                                    </div>
                                    <button class="tour-button">立即预订</button>
                                </div>
                            </div>
                        </div>
                        <div class="tour-card">
                            <div class="tour-img">
                                <img src="https://images.unsplash.com/photo-1540121732659-b7f91331be86?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1000&q=80" alt="三亚海岛度假五日游">
                                <div class="tour-badge">特惠</div>
                            </div>
                            <div class="tour-info">
                                <h3 class="tour-title">三亚海岛度假五日游</h3>
                                <div class="tour-meta">
                                    <span>5天4晚</span>
                                    <span>自由行</span>
                                </div>
                                <div class="tour-price">
                                    <div>
                                        <div class="tour-price-value">¥2,899 <small>¥3,599</small></div>
                                        <span style="font-size: 14px; color: #666;">已售2,156</span>
                                    </div>
                                    <button class="tour-button">立即预订</button>
                                </div>
                            </div>
                        </div>
                        <div class="tour-card">
                            <div class="tour-img">
                                <img src="https://images.unsplash.com/photo-1547981609-4b6bfe67ca03?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1000&q=80" alt="北京故宫长城文化之旅">
                                <div class="tour-badge">新品</div>
                            </div>
                            <div class="tour-info">
                                <h3 class="tour-title">北京故宫长城文化之旅</h3>
                                <div class="tour-meta">
                                    <span>4天3晚</span>
                                    <span>跟团游</span>
                                </div>
                                <div class="tour-price">
                                    <div>
                                        <div class="tour-price-value">¥2,299 <small>¥2,699</small></div>
                                        <span style="font-size: 14px; color: #666;">已售876</span>
                                    </div>
                                    <button class="tour-button">立即预订</button>
                                </div>
                            </div>
                        </div>
                        <div class="tour-card">
                            <div class="tour-img">
                                <img src="https://images.unsplash.com/photo-1565967511849-76a60a516170?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1000&q=80" alt="西藏拉萨林芝八日游">
                                <div class="tour-badge">畅销</div>
                            </div>
                            <div class="tour-info">
                                <h3 class="tour-title">西藏拉萨林芝八日游</h3>
                                <div class="tour-meta">
                                    <span>8天7晚</span>
                                    <span>跟团游</span>
                                </div>
                                <div class="tour-price">
                                    <div>
                                        <div class="tour-price-value">¥5,999 <small>¥6,599</small></div>
                                        <span style="font-size: 14px; color: #666;">已售632</span>
                                    </div>
                                    <button class="tour-button">立即预订</button>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
    <!-- 页脚 -->
    <footer class="footer">
        <div class="footer-container">
            <div class="footer-content">
                <div class="footer-column">
                    <h3>关于我们</h3>
                    <ul class="footer-links">
                        <li><a href="#">公司简介</a></li>
                        <li><a href="#">企业文化</a></li>
                        <li><a href="#">团队介绍</a></li>
                        <li><a href="#">发展历程</a></li>
                        <li><a href="#">招贤纳士</a></li>
                    </ul>
                </div>
                <div class="footer-column">
                    <h3>帮助中心</h3>
                    <ul class="footer-links">
                        <li><a href="#">预订须知</a></li>
                        <li><a href="#">付款方式</a></li>
                        <li><a href="#">签证服务</a></li>
                        <li><a href="#">常见问题</a></li>
                        <li><a href="#">旅游攻略</a></li>
                    </ul>
                </div>
                <div class="footer-column">
                    <h3>旅游服务</h3>
                    <ul class="footer-links">
                        <li><a href="#">跟团游</a></li>
                        <li><a href="#">自由行</a></li>
                        <li><a href="#">定制游</a></li>
                        <li><a href="#">酒店预订</a></li>
                        <li><a href="#">机票预订</a></li>
                    </ul>
                </div>
                <div class="footer-column">
                    <h3>联系我们</h3>
                    <ul class="footer-links">
                        <li><a href="#">客服电话：400-123-4567</a></li>
                        <li><a href="#">邮箱：service@lvtuwuyou.com</a></li>
                        <li><a href="#">地址：北京市朝阳区旅游大厦</a></li>
                        <li><a href="#">工作时间：9:00-18:00</a></li>
                    </ul>
                </div>
            </div>
            <div class="footer-bottom">
                <p>© 2024 旅途无忧 版权所有 | 京ICP备12345678号</p>
            </div>
        </div>
    </footer>
</body>
</html>
