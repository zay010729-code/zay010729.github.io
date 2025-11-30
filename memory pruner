<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>记忆修剪日志 - 阿克曼第18号</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            font-family: 'SimSun', '宋体', serif;
            background: linear-gradient(135deg, #1a1a2e 0%, #16213e 50%, #0f3460 100%);
            color: #e0e0e0;
            line-height: 1.8;
            min-height: 100vh;
            padding: 20px;
            position: relative;
            overflow-x: hidden;
        }
        
        body::before {
            content: '';
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: 
                radial-gradient(circle at 20% 30%, rgba(120, 119, 198, 0.1) 0%, transparent 50%),
                radial-gradient(circle at 80% 70%, rgba(255, 119, 198, 0.1) 0%, transparent 50%);
            pointer-events: none;
            z-index: -1;
        }
        
        .container {
            max-width: 800px;
            margin: 0 auto;
            background: rgba(25, 25, 35, 0.8);
            border: 1px solid rgba(255, 255, 255, 0.1);
            border-radius: 10px;
            padding: 40px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.5);
            position: relative;
            backdrop-filter: blur(10px);
        }
        
        .container::after {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: 
                linear-gradient(90deg, transparent 98%, rgba(255, 255, 255, 0.03) 100%),
                linear-gradient(rgba(0, 0, 0, 0.1) 50%, transparent 50%);
            background-size: 100% 2em, 100% 1px;
            pointer-events: none;
            z-index: 1;
        }
        
        .header {
            text-align: center;
            margin-bottom: 40px;
            border-bottom: 1px solid rgba(255, 255, 255, 0.2);
            padding-bottom: 20px;
            position: relative;
        }
        
        .title {
            font-size: 2.2em;
            color: #ff6b9d;
            text-shadow: 0 0 10px rgba(255, 107, 157, 0.5);
            margin-bottom: 10px;
            letter-spacing: 2px;
        }
        
        .subtitle {
            font-size: 1.1em;
            color: #89c4f4;
            font-style: italic;
        }
        
        .verse {
            margin: 25px 0;
            padding: 15px;
            border-left: 3px solid transparent;
            transition: all 0.3s ease;
            position: relative;
            z-index: 2;
        }
        
        .verse:hover {
            border-left-color: #ff6b9d;
            background: rgba(255, 107, 157, 0.05);
            transform: translateX(5px);
        }
        
        .verse-number {
            color: #89c4f4;
            font-size: 0.85em;
            display: inline-block;
            width: 50px;
            vertical-align: top;
            opacity: 0.7;
        }
        
        .verse-content {
            display: inline-block;
            width: calc(100% - 60px);
        }
        
        .highlight {
            color: #ff6b9d;
            text-shadow: 0 0 5px rgba(255, 107, 157, 0.3);
        }
        
        .scissor-icon {
            display: inline-block;
            margin: 0 5px;
            transform: rotate(45deg);
            color: #89c4f4;
        }
        
        .footer {
            text-align: center;
            margin-top: 50px;
            padding-top: 20px;
            border-top: 1px solid rgba(255, 255, 255, 0.2);
            color: #666;
            font-size: 0.9em;
        }
        
        .memory-button {
            background: rgba(255, 107, 157, 0.2);
            border: 1px solid rgba(255, 107, 157, 0.3);
            color: #ff6b9d;
            padding: 10px 20px;
            border-radius: 5px;
            cursor: pointer;
            transition: all 0.3s ease;
            margin: 10px;
        }
        
        .memory-button:hover {
            background: rgba(255, 107, 157, 0.3);
            transform: translateY(-2px);
        }
        
        /* 雪花屏效果 */
        .snow-effect {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: transparent;
            pointer-events: none;
            opacity: 0.02;
            z-index: -1;
        }
        
        .snow-effect::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: 
                repeating-linear-gradient(
                    0deg,
                    transparent,
                    transparent 2px,
                    white 2px,
                    white 4px
                );
            animation: snow 20s linear infinite;
        }
        
        @keyframes snow {
            0% { transform: translateY(-100%); }
            100% { transform: translateY(100%); }
        }
        
        /* 响应式设计 */
        @media (max-width: 768px) {
            .container {
                padding: 20px;
                margin: 10px;
            }
            
            .title {
                font-size: 1.8em;
            }
            
            .verse-number {
                width: 40px;
            }
            
            .verse-content {
                width: calc(100% - 50px);
            }
        }
        
        /* 打字机效果 */
        .typewriter {
            overflow: hidden;
            border-right: 2px solid #ff6b9d;
            white-space: nowrap;
            animation: typing 3.5s steps(40, end), blink-caret 0.75s step-end infinite;
        }
        
        @keyframes typing {
            from { width: 0 }
            to { width: 100% }
        }
        
        @keyframes blink-caret {
            from, to { border-color: transparent }
            50% { border-color: #ff6b9d }
        }
    </style>
</head>
<body>
    <div class="snow-effect"></div>
    
    <div class="container">
        <div class="header">
            <h1 class="title">记忆修剪日志</h1>
            <div class="subtitle">阿克曼 · 第18号记录</div>
        </div>
        
        <div class="content">
            <div class="verse">
                <span class="verse-number">M77</span>
                <span class="verse-content">我同时是<span class="highlight">凶手</span>与<span class="highlight">被害者</span></span>
            </div>
            <div class="verse">
                <span class="verse-number">M78</span>
                <span class="verse-content">也是<span class="highlight">修剪师</span>与<span class="highlight">客户</span></span>
            </div>
            <div class="verse">
                <span class="verse-number">M79</span>
                <span class="verse-content">更是<span class="highlight">遗忘</span>与<span class="highlight">记忆</span>的共生体</span>
            </div>
            <div class="verse">
                <span class="verse-number">M80</span>
                <span class="verse-content">弟弟把<span class="scissor-icon">✂</span>递给我，刀口朝他自己</span>
            </div>
            <div class="verse">
                <span class="verse-number">M81</span>
                <span class="verse-content">"这次，你剪断我，也剪断你自己"</span>
            </div>
            <div class="verse">
                <span class="verse-number">M82</span>
                <span class="verse-content">我接过<span class="scissor-icon">✂</span>，发现手柄上刻着：</span>
            </div>
            <div class="verse">
                <span class="verse-number">M83</span>
                <span class="verse-content">"<span class="highlight">勿停</span>"</span>
            </div>
            <div class="verse">
                <span class="verse-number">M84</span>
                <span class="verse-content">我大笑，笑声在倒悬图书馆产生回声</span>
            </div>
            <div class="verse">
                <span class="verse-number">M85</span>
                <span class="verse-content">回声落地，变成一本新的空册子</span>
            </div>
            <div class="verse">
                <span class="verse-number">M86</span>
                <span class="verse-content">封面写着：<span class="highlight">阿克曼，第18号修剪日志</span></span>
            </div>
            <div class="verse">
                <span class="verse-number">M87</span>
                <span class="verse-content">我把<span class="scissor-icon">✂</span>对准自己胸口，轻轻合上——</span>
            </div>
            <div class="verse">
                <span class="verse-number">M88</span>
                <span class="verse-content"><span class="highlight">喀</span></span>
            </div>
            <div class="verse">
                <span class="verse-number">M89</span>
                <span class="verse-content">樱桃味、铁锈味、鸽哨声同时熄灭</span>
            </div>
            <div class="verse">
                <span class="verse-number">M90</span>
                <span class="verse-content">世界退成黑白，我听见木片翻动的声音</span>
            </div>
            <div class="verse">
                <span class="verse-number">M91</span>
                <span class="verse-content">每一次翻动，都是一次遗忘的快门</span>
            </div>
            <div class="verse">
                <span class="verse-number">M92</span>
                <span class="verse-content">快门闭合，弟弟身影被裁成两半</span>
            </div>
            <div class="verse">
                <span class="verse-number">M93</span>
                <span class="verse-content">一半留在空册子，一半飞进我体内</span>
            </div>
            <div class="verse">
                <span class="verse-number">M94</span>
                <span class="verse-content">监测室的雪花屏突然恢复清晰</span>
            </div>
            <div class="verse">
                <span class="verse-number">M95</span>
                <span class="verse-content">脑纹接口读出新的报告：</span>
            </div>
            <div class="verse">
                <span class="verse-number">M96</span>
                <span class="verse-content">"客户17号记忆完整，新增创伤：0"</span>
            </div>
            <div class="verse">
                <span class="verse-number">M97</span>
                <span class="verse-content">"备注：修剪师林榭已被编入客户记忆，"</span>
            </div>
            <div class="verse">
                <span class="verse-number">M98</span>
                <span class="verse-content">"成为其弟弟的替身"</span>
            </div>
            <div class="verse">
                <span class="verse-number">M99</span>
                <span class="verse-content">我睁开眼，发现自己躺在监测椅</span>
            </div>
            <div class="verse">
                <span class="verse-number">M100</span>
                <span class="verse-content">助手递来一面小小的木镜：</span>
            </div>
            <div class="verse">
                <span class="verse-number">M101</span>
                <span class="verse-content">"这是客户送你的礼物"</span>
            </div>
            <div class="verse">
                <span class="verse-number">M102</span>
                <span class="verse-content">镜面空白，背面却刻着一行字：</span>
            </div>
            <div class="verse">
                <span class="verse-number">M103</span>
                <span class="verse-content">"请把我也放进你的记忆冢"</span>
            </div>
            <div class="verse">
                <span class="verse-number">M104</span>
                <span class="verse-content">我抬头，看见助手的眼睛闪过泪痣</span>
            </div>
            <div class="verse">
                <span class="verse-number">M105</span>
                <span class="verse-content">那位置，与弟弟一模一样</span>
            </div>
            <div class="verse">
                <span class="verse-number">M106</span>
                <span class="verse-content">我伸手去接木镜，指尖被木片划破</span>
            </div>
            <div class="verse">
                <span class="verse-number">M107</span>
                <span class="verse-content">血珠渗进木纹，像给记忆加了一层水印</span>
            </div>
            <div class="verse">
                <span class="verse-number">M108</span>
                <span class="verse-content">助手微笑，声音却来自弟弟：</span>
            </div>
            <div class="verse">
                <span class="verse-number">M109</span>
                <span class="verse-content">"姐姐，下次轮到我剪你了"</span>
            </div>
            <div class="verse">
                <span class="verse-number">M110</span>
                <span class="verse-content">我点头，把木镜塞进胸口抽屉</span>
            </div>
            <div class="verse">
                <span class="verse-number">M111</span>
                <span class="verse-content">那里早已堆满许多的回忆</span>
            </div>
            <div class="verse">
                <span class="verse-number">M112</span>
                <span class="verse-content">每一片都在等待下一次翻动</span>
            </div>
            <div class="verse">
                <span class="verse-number">M113</span>
                <span class="verse-content">每一次翻动，都是一次小小的坠落</span>
            </div>
            <div class="verse">
                <span class="verse-number">M114</span>
                <span class="verse-content">而坠落尽头，永远站着七岁的他</span>
            </div>
            <div class="verse">
                <span class="verse-number">M115</span>
                <span class="verse-content">举着樱桃核雕成的小船，对我说：</span>
            </div>
            <div class="verse">
                <span class="verse-number">M116</span>
                <span class="verse-content">"会回来找你"</span>
            </div>
            <div class="verse">
                <span class="verse-number">M117</span>
                <span class="verse-content">我关上抽屉，走出监测室</span>
            </div>
            <div class="verse">
                <span class="verse-number">M118</span>
                <span class="verse-content">走廊尽头的灯闪了一下，像鸽群起飞</span>
            </div>
            <div class="verse">
                <span class="verse-number">M119</span>
                <span class="verse-content">我低头，看见自己的影子长出泪痣</span>
            </div>
            <div class="verse">
                <span class="verse-number">M120</span>
                <span class="verse-content">它在我脚下轻轻跳动，像一颗备用心脏</span>
            </div>
            <div class="verse">
                <span class="verse-number">M121</span>
                <span class="verse-content">——记忆修剪完成——</span>
            </div>
            <div class="verse">
                <span class="verse-number">M122</span>
                <span class="verse-content">——记忆修剪从未完成——</span>
            </div>
            <div class="verse">
                <span class="verse-number">M123</span>
                <span class="verse-content">我抬头，把"完成"与"从未"同时写进日志</span>
            </div>
            <div class="verse">
                <span class="verse-number">M124</span>
                <span class="verse-content">然后合上笔帽，像合上<span class="scissor-icon">✂</span></span>
            </div>
            <div class="verse">
                <span class="verse-number">M125</span>
                <span class="verse-content"><span class="highlight">喀</span></span>
            </div>
            <div class="verse">
                <span class="verse-number">M126</span>
                <span class="verse-content">木片停止翻动，世界归于空白</span>
            </div>
            <div class="verse">
                <span class="verse-number">M127</span>
                <span class="verse-content">空白里，只剩樱桃核那么小的黑洞</span>
            </div>
            <div class="verse">
                <span class="verse-number">M128</span>
                <span class="verse-content">和黑洞里传来的下一声呼唤：</span>
            </div>
            <div class="verse">
                <span class="verse-number">M129</span>
                <span class="verse-content">"姐姐，该上班了"</span>
            </div>
            <div class="verse">
                <span class="verse-number">M130</span>
                <span class="verse-content">我转身，向黑洞走去</span>
            </div>
            <div class="verse">
                <span class="verse-number">M131</span>
                <span class="verse-content">背影在墙上被投成324行文字</span>
            </div>
            <div class="verse">
                <span class="verse-number">M132</span>
                <span class="verse-content">每行都在闪烁，像等待被翻动的木片</span>
            </div>
            <div class="verse">
                <span class="verse-number">M133</span>
                <span class="verse-content">我挥手，文字同时熄灭</span>
            </div>
            <div class="verse">
                <span class="verse-number">M134</span>
                <span class="verse-content">木镜复位，记忆归零</span>
            </div>
        </div>
        
        <div class="footer">
            <button class="memory-button" onclick="resetMemory()">重置记忆</button>
            <button class="memory-button" onclick="saveMemory()">保存日志</button>
            <p>记忆修剪系统 · 第18次循环</p>
        </div>
    </div>

    <script>
        // 交互效果
        function resetMemory() {
            document.querySelectorAll('.verse').forEach(verse => {
                verse.style.opacity = '0.3';
                setTimeout(() => {
                    verse.style.opacity = '1';
                    verse.style.transition = 'opacity 0.5s ease';
                }, 100);
            });
        }
        
        function saveMemory() {
            alert('记忆日志已保存至阿克曼档案库\n下次修剪时间：未知');
        }
        
        // 鼠标移动效果
        document.addEventListener('mousemove', (e) => {
            const verses = document.querySelectorAll('.verse');
            verses.forEach(verse => {
                const rect = verse.getBoundingClientRect();
                const x = e.clientX - rect.left;
                const y = e.clientY - rect.top;
                
                if (x > 0 && x < rect.width && y > 0 && y < rect.height) {
                    verse.style.transform = `translateX(5px) scale(1.02)`;
                } else {
                    verse.style.transform = `translateX(0) scale(1)`;
                }
            });
        });
        
        // 随机高亮效果
        setInterval(() => {
            const randomVerse = document.querySelectorAll('.verse')[Math.floor(Math.random() * document.querySelectorAll('.verse').length)];
            randomVerse.style.background = 'rgba(137, 196, 244, 0.1)';
            setTimeout(() => {
                randomVerse.style.background = '';
            }, 1000);
        }, 3000);
    </script>
</body>
</html>
