<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>图易改 - 在线图片格式与尺寸编辑器</title>
    <!-- 预留广告位：Google AdSense 或其他广告联盟代码可在此插入 -->
    <style>
        /* ===== 全局重置 & 字体 ===== */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;
            background: #f5f7fb;
            color: #1a1a2e;
            min-height: 100vh;
            display: flex;
            flex-direction: column;
        }

        /* ===== 顶部广告条 ===== */
        .ad-top {
            width: 100%;
            min-height: 60px;
            background: #eef1f5;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 14px;
            color: #888;
            border-bottom: 1px solid #e0e4ea;
            padding: 8px 16px;
            text-align: center;
        }
        .ad-top span {
            background: #fff;
            padding: 6px 24px;
            border-radius: 40px;
            box-shadow: 0 1px 4px rgba(0, 0, 0, 0.04);
        }

        /* ===== 主容器 ===== */
        .container {
            max-width: 1100px;
            margin: 30px auto 20px;
            padding: 0 24px;
            flex: 1;
            width: 100%;
        }

        /* ===== 头部 ===== */
        header {
            display: flex;
            align-items: center;
            justify-content: space-between;
            margin-bottom: 28px;
            flex-wrap: wrap;
            gap: 12px;
        }
        .logo h1 {
            font-size: 26px;
            font-weight: 700;
            letter-spacing: -0.5px;
            background: linear-gradient(135deg, #2563eb, #7c3aed);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }
        .logo small {
            font-size: 13px;
            font-weight: 400;
            color: #666;
            -webkit-text-fill-color: #666;
            margin-left: 6px;
        }
        .header-tip {
            font-size: 14px;
            color: #555;
            background: #fff;
            padding: 8px 18px;
            border-radius: 50px;
            box-shadow: 0 2px 8px rgba(0, 0, 0, 0.04);
        }

        /* ===== 卡片主体 ===== */
        .main-card {
            background: #ffffff;
            border-radius: 32px;
            box-shadow: 0 10px 48px rgba(0, 0, 0, 0.06);
            padding: 36px 34px 42px;
            transition: box-shadow 0.25s;
        }

        /* ===== 上传区域 ===== */
        .upload-zone {
            border: 2px dashed #d0d7e2;
            border-radius: 22px;
            padding: 44px 20px 38px;
            text-align: center;
            cursor: pointer;
            transition: all 0.25s;
            background: #fafcff;
            position: relative;
        }
        .upload-zone:hover {
            border-color: #2563eb;
            background: #f0f6ff;
        }
        .upload-zone.dragover {
            border-color: #2563eb;
            background: #e8f0fe;
        }
        .upload-zone .icon {
            font-size: 52px;
            line-height: 1;
            margin-bottom: 10px;
            opacity: 0.65;
        }
        .upload-zone p {
            font-size: 17px;
            font-weight: 500;
            color: #222;
        }
        .upload-zone .sub {
            font-size: 14px;
            color: #777;
            margin-top: 6px;
        }
        .upload-zone input[type="file"] {
            display: none;
        }
        .upload-zone .file-name {
            margin-top: 14px;
            font-size: 15px;
            color: #2563eb;
            font-weight: 500;
            word-break: break-all;
        }

        /* ===== 预览 + 控制区 ===== */
        .editor-area {
            display: flex;
            flex-wrap: wrap;
            gap: 32px;
            margin-top: 32px;
        }
        .preview-col {
            flex: 1 1 280px;
            min-width: 200px;
            display: flex;
            flex-direction: column;
            align-items: center;
        }
        .preview-col .label {
            font-size: 14px;
            font-weight: 600;
            color: #444;
            margin-bottom: 10px;
            align-self: flex-start;
        }
        .image-wrapper {
            width: 100%;
            border-radius: 18px;
            overflow: hidden;
            background: #f1f4fa;
            border: 1px solid #e9ecf2;
            display: flex;
            align-items: center;
            justify-content: center;
            min-height: 220px;
            max-height: 360px;
            transition: all 0.2s;
        }
        .image-wrapper img {
            max-width: 100%;
            max-height: 350px;
            object-fit: contain;
            display: block;
        }
        .image-wrapper .placeholder {
            color: #aaa;
            font-size: 15px;
            padding: 40px 20px;
            text-align: center;
        }
        .file-info {
            margin-top: 12px;
            font-size: 13px;
            color: #666;
            width: 100%;
            text-align: left;
            background: #f8faff;
            padding: 8px 14px;
            border-radius: 40px;
            border: 1px solid #eef2f8;
        }

        .controls-col {
            flex: 2 1 380px;
            min-width: 240px;
        }

        /* ===== 表单控件 ===== */
        .form-group {
            margin-bottom: 22px;
        }
        .form-group label {
            display: block;
            font-size: 14px;
            font-weight: 600;
            color: #333;
            margin-bottom: 6px;
        }
        .form-group .hint {
            font-size: 12px;
            color: #999;
            font-weight: 400;
            margin-left: 8px;
        }
        .row-duo {
            display: flex;
            gap: 18px;
            flex-wrap: wrap;
        }
        .row-duo .form-group {
            flex: 1 1 120px;
        }
        select,
        input[type="number"],
        input[type="text"] {
            width: 100%;
            padding: 10px 14px;
            border-radius: 14px;
            border: 1.5px solid #dce2ec;
            font-size: 15px;
            background: #fbfdff;
            transition: 0.2s;
            outline: none;
            font-family: inherit;
        }
        select:focus,
        input:focus {
            border-color: #2563eb;
            box-shadow: 0 0 0 3px rgba(37, 99, 235, 0.12);
        }
        input[type="number"] {
            -moz-appearance: textfield;
        }
        input[type="number"]::-webkit-inner-spin-button,
        input[type="number"]::-webkit-outer-spin-button {
            -webkit-appearance: none;
        }
        .checkbox-group {
            display: flex;
            align-items: center;
            gap: 10px;
            margin-top: 4px;
        }
        .checkbox-group input[type="checkbox"] {
            width: 19px;
            height: 19px;
            accent-color: #2563eb;
            cursor: pointer;
        }
        .checkbox-group label {
            font-weight: 450;
            font-size: 14px;
            color: #444;
            cursor: pointer;
            margin-bottom: 0;
        }

        /* ===== 操作按钮 ===== */
        .actions {
            display: flex;
            flex-wrap: wrap;
            gap: 14px;
            margin-top: 22px;
            border-top: 1px solid #eff2f8;
            padding-top: 26px;
        }
        .btn {
            padding: 12px 32px;
            border-radius: 80px;
            border: none;
            font-size: 16px;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.2s;
            display: inline-flex;
            align-items: center;
            justify-content: center;
            gap: 8px;
            background: #f0f4fe;
            color: #1a2b4c;
            flex: 1 1 auto;
            min-width: 130px;
        }
        .btn-primary {
            background: #2563eb;
            color: #fff;
            box-shadow: 0 4px 14px rgba(37, 99, 235, 0.25);
        }
        .btn-primary:hover {
            background: #1d4ed8;
            transform: translateY(-2px);
            box-shadow: 0 8px 24px rgba(37, 99, 235, 0.30);
        }
        .btn-primary:disabled {
            opacity: 0.45;
            cursor: not-allowed;
            transform: none;
            box-shadow: none;
        }
        .btn-secondary {
            background: #eef2f8;
            color: #333;
        }
        .btn-secondary:hover {
            background: #e2e8f0;
        }
        .btn-success {
            background: #0f973d;
            color: #fff;
            box-shadow: 0 4px 14px rgba(15, 151, 61, 0.20);
        }
        .btn-success:hover {
            background: #0d7e33;
            transform: translateY(-2px);
        }
        .btn-success:disabled {
            opacity: 0.45;
            cursor: not-allowed;
            transform: none;
            box-shadow: none;
        }

        /* ===== 底部广告 ===== */
        .ad-bottom {
            margin-top: 30px;
            width: 100%;
            min-height: 70px;
            background: #eef1f5;
            border-radius: 20px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 14px;
            color: #888;
            border: 1px solid #e4e9f0;
            padding: 12px 20px;
            text-align: center;
        }
        .ad-bottom span {
            background: #fff;
            padding: 8px 28px;
            border-radius: 40px;
            box-shadow: 0 1px 4px rgba(0, 0, 0, 0.03);
        }

        /* ===== Footer ===== */
        footer {
            text-align: center;
            padding: 20px 24px 28px;
            font-size: 13px;
            color: #999;
            border-top: 1px solid #eceff5;
            margin-top: 18px;
        }
        footer a {
            color: #666;
            text-decoration: none;
        }

        /* ===== Toast 提示 ===== */
        .toast {
            position: fixed;
            bottom: 35px;
            left: 50%;
            transform: translateX(-50%);
            background: #1a1a2e;
            color: #fff;
            padding: 14px 32px;
            border-radius: 60px;
            font-size: 15px;
            font-weight: 460;
            box-shadow: 0 8px 32px rgba(0, 0, 0, 0.18);
            opacity: 0;
            transition: opacity 0.3s ease, transform 0.3s ease;
            pointer-events: none;
            z-index: 999;
            white-space: nowrap;
            max-width: 90vw;
            overflow: hidden;
            text-overflow: ellipsis;
        }
        .toast.show {
            opacity: 1;
            pointer-events: auto;
        }

        /* ===== 响应式 ===== */
        @media (max-width: 640px) {
            .container {
                padding: 0 12px;
                margin-top: 16px;
            }
            .main-card {
                padding: 22px 16px 28px;
                border-radius: 24px;
            }
            .upload-zone {
                padding: 30px 14px 26px;
            }
            .editor-area {
                gap: 20px;
            }
            .actions {
                flex-direction: column;
            }
            .btn {
                width: 100%;
                padding: 14px 20px;
            }
            header {
                flex-direction: column;
                align-items: flex-start;
            }
            .header-tip {
                font-size: 13px;
                padding: 6px 16px;
            }
            .ad-top span,
            .ad-bottom span {
                font-size: 12px;
                padding: 6px 16px;
            }
        }
    </style>
</head>
<body>

    <!-- ===== 顶部广告位 ===== -->
    <div class="ad-top">
        <span>📢 广告位招商 — 联系站长投放优质广告</span>
    </div>

    <div class="container">

        <!-- ===== 头部 ===== -->
        <header>
            <div class="logo">
                <h1>🖼️ 图易改 <small>在线 · 免费 · 秒改</small></h1>
            </div>
            <div class="header-tip">⚡ 拖拽上传 · 一键转换 · 精准调像素</div>
        </header>

        <!-- ===== 主卡片 ===== -->
        <div class="main-card">

            <!-- 上传区域 -->
            <div class="upload-zone" id="dropZone">
                <div class="icon">📁</div>
                <p>点击上传 或 拖拽图片到这里</p>
                <div class="sub">支持 JPG / PNG / WebP / BMP / GIF</div>
                <input type="file" id="fileInput" accept="image/*" />
                <div class="file-name" id="fileName"></div>
            </div>

            <!-- 编辑器 -->
            <div class="editor-area" id="editorArea" style="display:none;">
                <!-- 预览列 -->
                <div class="preview-col">
                    <div class="label">👀 预览</div>
                    <div class="image-wrapper" id="imageWrapper">
                        <img id="previewImage" alt="预览" />
                    </div>
                    <div class="file-info" id="fileInfo">—</div>
                </div>

                <!-- 控制列 -->
                <div class="controls-col">
                    <!-- 格式 -->
                    <div class="form-group">
                        <label>输出格式</label>
                        <select id="formatSelect">
                            <option value="png">PNG (无损)</option>
                            <option value="jpeg" selected>JPEG (兼容性好)</option>
                            <option value="webp">WebP (体积小)</option>
                            <option value="bmp">BMP (未压缩)</option>
                            <option value="gif">GIF (动图/静态)</option>
                        </select>
                    </div>

                    <!-- 尺寸 -->
                    <div class="row-duo">
                        <div class="form-group">
                            <label>宽度 (px)</label>
                            <input type="number" id="widthInput" min="1" max="10000" placeholder="自动" />
                        </div>
                        <div class="form-group">
                            <label>高度 (px)</label>
                            <input type="number" id="heightInput" min="1" max="10000" placeholder="自动" />
                        </div>
                    </div>

                    <!-- 锁定比例 -->
                    <div class="checkbox-group">
                        <input type="checkbox" id="lockRatio" checked />
                        <label for="lockRatio">🔒 锁定宽高比</label>
                    </div>

                    <!-- 操作按钮 -->
                    <div class="actions">
                        <button class="btn btn-primary" id="processBtn">✨ 开始处理</button>
                        <button class="btn btn-success" id="downloadBtn" disabled>⬇️ 下载图片</button>
                        <button class="btn btn-secondary" id="resetBtn">🔄 重置</button>
                    </div>

                    <div style="margin-top: 16px; font-size: 13px; color: #888; border-top: 1px dashed #e8ecf4; padding-top: 16px;">
                        💡 留空宽高则保持原尺寸；只填一项按比例缩放。
                    </div>
                </div>
            </div>

            <!-- 无图片时的占位提示 -->
            <div id="emptyState" style="text-align:center; padding: 30px 0 10px; color:#aaa;">
                <span style="font-size:18px;">⬆️ 请先上传一张图片</span>
            </div>
        </div>

        <!-- ===== 底部广告位 ===== -->
        <div class="ad-bottom">
            <span>🎯 广告位招租 · 精准流量 · 欢迎合作</span>
        </div>

    </div>

    <!-- ===== Footer ===== -->
    <footer>
        <p>图易改 · 让图片修改更简单 &nbsp;|&nbsp; 仅供个人学习使用 &nbsp;·&nbsp; <a href="#">隐私政策</a></p>
    </footer>

    <!-- ===== Toast ===== -->
    <div class="toast" id="toast"></div>

    <script>
        // ============================================================
        //  核心逻辑
        // ============================================================

        (function() {
            'use strict';

            // DOM 引用
            const dropZone = document.getElementById('dropZone');
            const fileInput = document.getElementById('fileInput');
            const fileName = document.getElementById('fileName');
            const editorArea = document.getElementById('editorArea');
            const emptyState = document.getElementById('emptyState');
            const previewImage = document.getElementById('previewImage');
            const imageWrapper = document.getElementById('imageWrapper');
            const fileInfo = document.getElementById('fileInfo');

            const formatSelect = document.getElementById('formatSelect');
            const widthInput = document.getElementById('widthInput');
            const heightInput = document.getElementById('heightInput');
            const lockRatio = document.getElementById('lockRatio');

            const processBtn = document.getElementById('processBtn');
            const downloadBtn = document.getElementById('downloadBtn');
            const resetBtn = document.getElementById('resetBtn');

            const toast = document.getElementById('toast');

            // ---- 状态 ----
            let sourceFile = null; // 原始 File
            let sourceImage = null; // new Image()
            let originalWidth = 0;
            let originalHeight = 0;
            let processedBlobUrl = null; // 处理后的 blob url

            // ---- 辅助函数 ----
            function showToast(msg, duration = 2600) {
                toast.textContent = msg;
                toast.classList.add('show');
                clearTimeout(toast._timer);
                toast._timer = setTimeout(() => {
                    toast.classList.remove('show');
                }, duration);
            }

            function formatBytes(bytes) {
                if (bytes < 1024) return bytes + ' B';
                if (bytes < 1048576) return (bytes / 1024).toFixed(1) + ' KB';
                return (bytes / 1048576).toFixed(2) + ' MB';
            }

            // 更新文件信息展示
            function updateFileInfo(file, w, h) {
                if (!file) {
                    fileInfo.textContent = '—';
                    return;
                }
                const name = file.name;
                const size = formatBytes(file.size);
                const dims = (w && h) ? `${w} × ${h} px` : '? × ?';
                fileInfo.textContent = `${name} · ${size} · ${dims}`;
            }

            // 显示/隐藏编辑器
            function toggleEditor(show) {
                if (show) {
                    editorArea.style.display = 'flex';
                    emptyState.style.display = 'none';
                } else {
                    editorArea.style.display = 'none';
                    emptyState.style.display = 'block';
                }
            }

            // 重置控件 (保留上传状态)
            function resetControls() {
                widthInput.value = '';
                heightInput.value = '';
                formatSelect.value = 'jpeg';
                lockRatio.checked = true;
                downloadBtn.disabled = true;
                if (processedBlobUrl) {
                    URL.revokeObjectURL(processedBlobUrl);
                    processedBlobUrl = null;
                }
                // 如果还有源图，预览恢复源图
                if (sourceImage) {
                    previewImage.src = sourceImage.src;
                    updateFileInfo(sourceFile, originalWidth, originalHeight);
                }
            }

            // ---- 加载图片 ----
            function loadImageFromFile(file) {
                if (!file || !file.type.startsWith('image/')) {
                    showToast('⚠️ 请选择有效的图片文件');
                    return;
                }

                // 限制大小 20MB
                if (file.size > 20 * 1024 * 1024) {
                    showToast('📦 图片超过 20MB，请压缩后重试');
                    return;
                }

                sourceFile = file;
                fileName.textContent = `📄 ${file.name}`;

                const reader = new FileReader();
                reader.onload = function(e) {
                    const img = new Image();
                    img.onload = function() {
                        sourceImage = img;
                        originalWidth = img.naturalWidth;
                        originalHeight = img.naturalHeight;

                        // 显示预览
                        previewImage.src = img.src;
                        updateFileInfo(sourceFile, originalWidth, originalHeight);

                        // 显示编辑器
                        toggleEditor(true);
                        resetControls();

                        // 自动填充宽高
                        widthInput.value = originalWidth;
                        heightInput.value = originalHeight;

                        showToast(`✅ 已加载：${originalWidth} × ${originalHeight}`);
                    };
                    img.onerror = function() {
                        showToast('❌ 图片加载失败，请检查文件');
                    };
                    img.src = e.target.result;
                };
                reader.readAsDataURL(file);
            }

            // ---- 上传触发 ----
            function triggerUpload(files) {
                if (!files || files.length === 0) return;
                const file = files[0];
                // 清理之前的 blob
                if (processedBlobUrl) {
                    URL.revokeObjectURL(processedBlobUrl);
                    processedBlobUrl = null;
                }
                loadImageFromFile(file);
            }

            // ---- 事件绑定：上传 ----
            dropZone.addEventListener('click', () => {
                fileInput.click();
            });
            fileInput.addEventListener('change', (e) => {
                triggerUpload(e.target.files);
                fileInput.value = ''; // 允许重复选同一文件
            });

            // 拖拽
            dropZone.addEventListener('dragover', (e) => {
                e.preventDefault();
                dropZone.classList.add('dragover');
            });
            dropZone.addEventListener('dragleave', () => {
                dropZone.classList.remove('dragover');
            });
            dropZone.addEventListener('drop', (e) => {
                e.preventDefault();
                dropZone.classList.remove('dragover');
                const files = e.dataTransfer.files;
                if (files.length > 0) {
                    triggerUpload(files);
                }
            });

            // ---- 锁定比例逻辑 ----
            let ratioLocking = false; // 防止循环

            function getAspectRatio() {
                if (originalWidth && originalHeight) {
                    return originalWidth / originalHeight;
                }
                return 1;
            }

            widthInput.addEventListener('input', function() {
                if (!lockRatio.checked || ratioLocking) return;
                const w = parseInt(this.value);
                if (w > 0 && originalHeight) {
                    ratioLocking = true;
                    const ratio = getAspectRatio();
                    const h = Math.round(w / ratio);
                    heightInput.value = h;
                    ratioLocking = false;
                }
            });

            heightInput.addEventListener('input', function() {
                if (!lockRatio.checked || ratioLocking) return;
                const h = parseInt(this.value);
                if (h > 0 && originalWidth) {
                    ratioLocking = true;
                    const ratio = getAspectRatio();
                    const w = Math.round(h * ratio);
                    widthInput.value = w;
                    ratioLocking = false;
                }
            });

            lockRatio.addEventListener('change', function() {
                if (this.checked) {
                    // 立即同步一次
                    const w = parseInt(widthInput.value);
                    if (w > 0) {
                        const ratio = getAspectRatio();
                        heightInput.value = Math.round(w / ratio);
                    } else {
                        const h = parseInt(heightInput.value);
                        if (h > 0) {
                            widthInput.value = Math.round(h * getAspectRatio());
                        }
                    }
                }
            });

            // ---- 处理图片 (核心) ----
            function processImage() {
                if (!sourceImage) {
                    showToast('⚠️ 请先上传图片');
                    return;
                }

                const format = formatSelect.value;
                let targetW = parseInt(widthInput.value);
                let targetH = parseInt(heightInput.value);

                // 校验宽高
                if (targetW && targetH) {
                    // 都填了，直接用
                } else if (targetW && !targetH) {
                    // 按宽度等比
                    targetH = Math.round(targetW / getAspectRatio());
                    heightInput.value = targetH;
                } else if (!targetW && targetH) {
                    // 按高度等比
                    targetW = Math.round(targetH * getAspectRatio());
                    widthInput.value = targetW;
                } else {
                    // 都没填，使用原尺寸
                    targetW = originalWidth;
                    targetH = originalHeight;
                    widthInput.value = targetW;
                    heightInput.value = targetH;
                }

                // 边界保护
                if (targetW < 1) targetW = 1;
                if (targetH < 1) targetH = 1;
                if (targetW > 10000 || targetH > 10000) {
                    showToast('⚠️ 尺寸不能超过 10000×10000');
                    return;
                }

                // 创建 canvas
                const canvas = document.createElement('canvas');
                canvas.width = targetW;
                canvas.height = targetH;
                const ctx = canvas.getContext('2d');

                // 绘制 (平滑缩放)
                ctx.imageSmoothingEnabled = true;
                ctx.imageSmoothingQuality = 'high';
                ctx.drawImage(sourceImage, 0, 0, targetW, targetH);

                // 导出
                let mimeType = 'image/png';
                let ext = 'png';
                switch (format) {
                    case 'jpeg':
                        mimeType = 'image/jpeg';
                        ext = 'jpg';
                        break;
                    case 'webp':
                        mimeType = 'image/webp';
                        ext = 'webp';
                        break;
                    case 'bmp':
                        mimeType = 'image/bmp';
                        ext = 'bmp';
                        break;
                    case 'gif':
                        mimeType = 'image/gif';
                        ext = 'gif';
                        break;
                    default:
                        mimeType = 'image/png';
                        ext = 'png';
                }

                // JPEG 默认 0.92 质量
                const quality = (format === 'jpeg') ? 0.92 : undefined;

                try {
                    const dataUrl = canvas.toDataURL(mimeType, quality);
                    // 转换为 blob
                    const byteString = atob(dataUrl.split(',')[1]);
                    const ab = new ArrayBuffer(byteString.length);
                    const ia = new Uint8Array(ab);
                    for (let i = 0; i < byteString.length; i++) {
                        ia[i] = byteString.charCodeAt(i);
                    }
                    const blob = new Blob([ab], { type: mimeType });

                    // 释放旧 blob
                    if (processedBlobUrl) {
                        URL.revokeObjectURL(processedBlobUrl);
                    }
                    processedBlobUrl = URL.createObjectURL(blob);

                    // 更新预览
                    previewImage.src = processedBlobUrl;

                    // 更新文件信息 (显示新尺寸)
                    const fakeFile = new File([blob], `output.${ext}`, { type: mimeType });
                    updateFileInfo(fakeFile, targetW, targetH);

                    // 启用下载
                    downloadBtn.disabled = false;

                    showToast(`✅ 处理完成！${targetW} × ${targetH} · 格式 ${format.toUpperCase()}`, 1800);
                } catch (err) {
                    showToast('❌ 处理失败：' + err.message);
                    console.error(err);
                }
            }

            // ---- 下载 ----
            function downloadImage() {
                if (!processedBlobUrl) {
                    showToast('⚠️ 请先处理图片');
                    return;
                }
                const format = formatSelect.value;
                const extMap = { png: 'png', jpeg: 'jpg', webp: 'webp', bmp: 'bmp', gif: 'gif' };
                const ext = extMap[format] || 'png';
                const filename = `图易改_${Date.now()}.${ext}`;

                const a = document.createElement('a');
                a.href = processedBlobUrl;
                a.download = filename;
                document.body.appendChild(a);
                a.click();
                document.body.removeChild(a);
                showToast('⬇️ 下载已开始');
            }

            // ---- 重置 ----
            function resetAll() {
                if (processedBlobUrl) {
                    URL.revokeObjectURL(processedBlobUrl);
                    processedBlobUrl = null;
                }
                if (sourceImage) {
                    previewImage.src = sourceImage.src;
                    updateFileInfo(sourceFile, originalWidth, originalHeight);
                    widthInput.value = originalWidth;
                    heightInput.value = originalHeight;
                }
                formatSelect.value = 'jpeg';
                lockRatio.checked = true;
                downloadBtn.disabled = true;
                showToast('🔄 已重置为原始状态');
            }

            // ---- 按钮事件 ----
            processBtn.addEventListener('click', processImage);
            downloadBtn.addEventListener('click', downloadImage);
            resetBtn.addEventListener('click', resetAll);

            // ---- 快捷键 ----
            document.addEventListener('keydown', (e) => {
                if ((e.ctrlKey || e.metaKey) && e.key === 'Enter') {
                    e.preventDefault();
                    processImage();
                }
            });

            // ---- 初始化 ----
            toggleEditor(false);
            showToast('🖼️ 上传图片开始编辑', 1600);

            // 暴露一些变量方便调试 (非必须)
            window.__app = { processImage, downloadImage, resetAll };

        })();
    </script>

</body>
</html>
