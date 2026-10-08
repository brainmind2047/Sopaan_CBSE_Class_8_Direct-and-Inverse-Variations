<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<title>Sopaan · Direct and Inverse Variations</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Fraunces:opsz,wght@9..144,500;9..144,700&family=Source+Sans+3:wght@400;600;700&family=IBM+Plex+Mono:wght@500;600&display=swap">
<style>
  html,body{margin:0;} img{max-width:100%;} [hidden]{display:none !important;}
  :root{
    --navy:#16264A; --navy-2:#1F3B6B; --gold:#C79A3E; --gold-soft:#F3E7C9;
    --paper:#FBF9F4; --paper-2:#F1EAD8; --card:#FFFFFF;
    --ink:#211E1A; --ink-soft:#655D4C; --rule:#E4DCC8;
    --success:#2E8B57; --success-soft:#E1F2E7;
    --danger:#BF4B45; --danger-soft:#FAE3E1;
    --locked:#C7BEA9;
    --focus:#1F3B6B;
    --accent-text:#1F3B6B; --retry-text:#8A661F;
    color-scheme:light;
  }
  @media (prefers-color-scheme: dark){
    :root:not([data-theme="light"]){
      --navy:#0E1830; --navy-2:#16264A; --gold:#E0B75B; --gold-soft:#3A2F16;
      --paper:#141210; --paper-2:#1C1914; --card:#1C1914;
      --ink:#EDE7DA; --ink-soft:#B2A996; --rule:#3A342A;
      --success:#7BC79A; --success-soft:#1B2E22;
      --danger:#E38884; --danger-soft:#331D1B;
      --locked:#4A4436;
      --focus:#E0B75B;
      --accent-text:#E0B75B; --retry-text:#E0B75B;
      color-scheme:dark;
    }
  }
  :root[data-theme="dark"]{
    --navy:#0E1830; --navy-2:#16264A; --gold:#E0B75B; --gold-soft:#3A2F16;
    --paper:#141210; --paper-2:#1C1914; --card:#1C1914;
    --ink:#EDE7DA; --ink-soft:#B2A996; --rule:#3A342A;
    --success:#7BC79A; --success-soft:#1B2E22;
    --danger:#E38884; --danger-soft:#331D1B;
    --locked:#4A4436;
    --focus:#E0B75B;
    --accent-text:#E0B75B; --retry-text:#E0B75B;
    color-scheme:dark;
  }

  *{box-sizing:border-box;}
  body{background:var(--paper); color:var(--ink); font-family:'Source Sans 3',-apple-system,'Segoe UI',sans-serif; padding-inline:0; padding-block:0;}
  h1,h2,h3{font-family:'Fraunces',Georgia,serif; text-wrap:balance; margin:0;}
  .num{font-family:'IBM Plex Mono',ui-monospace,monospace; font-variant-numeric:tabular-nums;}

  header.brand{
    background:linear-gradient(155deg,var(--navy) 0%, var(--navy-2) 100%);
    color:#F4EFDF; padding-block:calc(20px + env(safe-area-inset-top,0px)) 18px; padding-inline:20px;
  }
  .brand-row{display:flex; align-items:center; gap:12px; max-width:900px; margin:0 auto;}
  .crest{
    width:42px; height:42px; border-radius:10px; background:var(--gold); color:var(--navy);
    display:flex; align-items:center; justify-content:center; font-family:'Fraunces',serif; font-weight:700; font-size:18px; flex-shrink:0;
  }
  .brand-name{font-size:12px; letter-spacing:.08em; text-transform:uppercase; color:var(--gold); font-weight:700;}
  .series-name{font-size:19px; font-weight:700; font-family:'Fraunces',serif;}
  .chapter-eyebrow{max-width:900px; margin:14px auto 0; font-size:12px; letter-spacing:.06em; text-transform:uppercase; color:#AEB9D6;}
  .chapter-title{font-size:28px; max-width:900px; margin:2px auto 0;}
  .chapter-sub{font-size:14.5px; color:var(--gold); font-weight:700; max-width:900px; margin:3px auto 0;}

  .chapter-progress{max-width:900px; margin:14px auto 0; display:flex; align-items:center; gap:10px;}
  .cp-track{flex:1; height:6px; border-radius:99px; background:rgba(255,255,255,.18); overflow:hidden;}
  .cp-fill{height:100%; background:var(--gold); border-radius:99px; transition:width .3s ease;}
  .cp-label{font-size:11.5px; color:#CFD7EA; white-space:nowrap;}

  .tabbar{position:sticky; top:env(safe-area-inset-top,0px); z-index:15; background:var(--paper); border-bottom:1px solid var(--rule); overflow-x:auto; white-space:nowrap;}
  .tabbar-inner{max-width:900px; margin:0 auto; display:flex; padding-inline:16px;}
  .tab-btn{font-family:inherit; font-size:14px; font-weight:600; color:var(--ink-soft); background:none; border:none; padding:13px 16px; cursor:pointer; position:relative; flex-shrink:0;}
  .tab-btn.active{color:var(--accent-text);}
  .tab-btn.active::after{content:''; position:absolute; left:12px; right:12px; bottom:0; height:3px; background:var(--gold); border-radius:3px 3px 0 0;}
  .tab-count{font-size:11px; color:var(--ink-soft); margin-left:5px;}

  .slide-progress{max-width:900px; margin:0 auto; padding:10px 16px 0; display:flex; align-items:center; gap:10px;}
  .sp-track{flex:1; height:5px; border-radius:99px; background:var(--rule); overflow:hidden;}
  .sp-fill{height:100%; background:var(--accent-text); border-radius:99px; transition:width .3s ease;}
  .sp-label{font-size:12px; color:var(--ink-soft); white-space:nowrap; font-weight:600;}

  .wrap{max-width:900px; margin:0 auto; padding:16px 16px calc(110px + env(safe-area-inset-bottom,0px));}

  .qcard{background:var(--card); border:1px solid var(--rule); border-radius:14px; padding:18px;}
  .qhead{display:flex; align-items:flex-start; gap:10px; margin-bottom:10px;}
  .qnum{width:32px; height:32px; border-radius:8px; background:var(--gold-soft); color:var(--accent-text); display:flex; align-items:center; justify-content:center; font-weight:700; font-family:'Fraunces',serif; flex-shrink:0; font-size:14px;}
  .qtext{font-size:16px; line-height:1.55; flex:1;}
  .qtag{font-size:10.5px; color:var(--gold); background:var(--gold-soft); padding:2px 7px; border-radius:99px; font-weight:700; margin-left:6px; white-space:nowrap;}
  .marks-pill{font-size:11px; font-weight:700; color:var(--ink-soft); border:1px solid var(--rule); padding:3px 9px; border-radius:99px; margin-left:auto; flex-shrink:0; white-space:nowrap;}
  .step-badge{font-size:11px; font-weight:700; color:var(--accent-text); background:var(--paper-2); border:1px solid var(--rule); padding:3px 9px; border-radius:99px; display:inline-block; margin-bottom:12px;}

  .options{display:flex; flex-direction:column; gap:8px; margin-top:10px;}
  .opt{display:flex; align-items:center; gap:10px; padding:11px 12px; border:1.5px solid var(--rule); border-radius:10px; cursor:pointer; font-size:15px; background:var(--paper);}
  .opt input{accent-color:var(--navy-2);}
  .opt.is-correct{border-color:var(--success); background:var(--success-soft);}
  .opt.is-wrong{border-color:var(--danger); background:var(--danger-soft);}
  .opt.locked{cursor:not-allowed;}

  .subpart-label{font-weight:700; font-size:12.5px; color:var(--accent-text); text-transform:uppercase; letter-spacing:.03em; margin:14px 0 6px;}
  .or-divider{text-align:center; font-size:11px; font-weight:700; letter-spacing:.08em; color:var(--ink-soft); margin:8px 0;}

  .steps{display:flex; flex-direction:column; gap:10px;}
  .step-line{font-size:14.5px; line-height:1.9; background:var(--paper); border:1px dashed var(--rule); border-radius:10px; padding:9px 12px;}
  .step-line.resolved{opacity:.9;}
  .blank-input{font-family:'IBM Plex Mono',monospace; font-size:14px; border:1.5px solid var(--rule); border-radius:6px; padding:3px 8px; width:120px; background:var(--card); color:var(--ink); margin:0 2px;}
  .blank-input:focus{outline:none; border-color:var(--focus); box-shadow:0 0 0 3px var(--gold-soft);}
  .blank-input.is-correct{border-color:var(--success); background:var(--success-soft);}
  .blank-input.is-wrong{border-color:var(--danger); background:var(--danger-soft);}
  .blank-input[disabled]{opacity:.85;}
  .reveal-note{font-size:12px; color:var(--danger); padding-left:2px; margin-top:-2px;}

  .feedback{font-size:13.5px; padding:10px 12px; border-radius:9px; margin-top:14px; display:none;}
  .feedback.show{display:block;}
  .feedback.ok{background:var(--success-soft); color:var(--success);}
  .feedback.retry{background:var(--gold-soft); color:var(--retry-text);}
  .feedback.reveal{background:var(--danger-soft); color:var(--danger);}
  .feedback.err{background:var(--danger-soft); color:var(--danger);}
  .attempts-dots{display:inline-flex; gap:4px; margin-left:2px;}
  .attempts-dots span{width:6px; height:6px; border-radius:50%; background:var(--ink-soft); opacity:.3; display:inline-block;}
  .attempts-dots span.used{opacity:1; background:var(--danger);}

  .ar-box{background:var(--paper-2); border-radius:10px; padding:10px 12px; margin-bottom:12px; font-size:13px; color:var(--ink-soft);}

  .navbar{
    position:fixed; left:0; right:0; bottom:0; z-index:30; background:var(--paper);
    border-top:1px solid var(--rule); padding:10px 16px calc(10px + env(safe-area-inset-bottom,0px));
  }
  .navbar-inner{max-width:900px; margin:0 auto; display:flex; gap:8px; flex-wrap:wrap; align-items:center;}
  .btn{font-family:inherit; font-size:13.5px; font-weight:700; padding:10px 14px; border-radius:9px; border:1.5px solid var(--rule); background:var(--card); color:var(--ink); cursor:pointer;}
  .btn:hover{border-color:var(--navy-2);}
  .btn:disabled{opacity:.4; cursor:not-allowed;}
  .btn-primary{background:var(--navy-2); color:#fff; border-color:var(--navy-2);}
  .navbar .spacer{flex:1;}

  .fab{position:fixed; right:16px; bottom:calc(74px + env(safe-area-inset-bottom,0px)); background:var(--gold); color:var(--navy); border:none; border-radius:999px; padding:11px 16px; font-family:inherit; font-weight:700; font-size:13px; display:flex; align-items:center; gap:7px; cursor:pointer; box-shadow:0 6px 16px rgba(0,0,0,.18); z-index:35;}
  .fab-badge{background:rgba(255,255,255,.55); border-radius:99px; padding:1px 7px; font-size:11px;}

  .overlay{position:fixed; inset:0; background:rgba(20,18,14,.45); z-index:50; display:none; align-items:flex-end; justify-content:center;}
  .overlay.show{display:flex;}
  .palette{background:var(--card); width:min(480px,100%); max-height:78vh; overflow-y:auto; border-radius:18px 18px 0 0; padding:18px 18px calc(18px + env(safe-area-inset-bottom,0px)); border:1px solid var(--rule); border-bottom:none;}
  @media (min-width:640px){ .overlay{align-items:center;} .palette{border-radius:18px; border-bottom:1px solid var(--rule); max-height:74vh;} }
  .palette-head{display:flex; align-items:center; justify-content:space-between; margin-bottom:6px;}
  .palette-head h2{font-size:16px;}
  .palette-close{background:none; border:none; font-size:20px; color:var(--ink-soft); cursor:pointer; padding:4px;}
  .palette-legend{display:flex; gap:12px; flex-wrap:wrap; font-size:11px; color:var(--ink-soft); margin:10px 0 14px;}
  .palette-legend span{display:inline-flex; align-items:center; gap:5px;}
  .dot{width:9px; height:9px; border-radius:50%; display:inline-block;}
  .dot.correct{background:var(--success);} .dot.revealed{background:var(--danger);}
  .dot.skipped{background:var(--gold);} .dot.locked{background:var(--locked);}
  .dot.current{background:var(--navy-2);}
  .chip-grid{display:grid; grid-template-columns:repeat(auto-fill,minmax(48px,1fr)); gap:8px;}
  .chip{border:1.5px solid var(--rule); border-radius:9px; padding:8px 4px; text-align:center; font-family:'IBM Plex Mono',monospace; font-size:12.5px; font-weight:600; cursor:pointer; background:var(--paper); color:var(--ink);}
  .chip[data-status="correct"]{border-color:var(--success); background:var(--success-soft); color:var(--success);}
  .chip[data-status="revealed"]{border-color:var(--danger); background:var(--danger-soft); color:var(--danger);}
  .chip[data-status="skipped"]{border-color:var(--gold); background:var(--gold-soft); color:var(--retry-text);}
  .chip[data-status="locked"]{border-color:var(--rule); color:var(--locked); cursor:not-allowed; background:var(--paper-2);}
  .chip[data-status="current"]{outline:2px solid var(--navy-2); outline-offset:1px;}

  .toast{position:fixed; left:50%; bottom:calc(140px + env(safe-area-inset-bottom,0px)); transform:translateX(-50%); background:var(--ink); color:var(--paper); padding:9px 16px; border-radius:99px; font-size:13px; opacity:0; pointer-events:none; transition:opacity .25s ease; z-index:60;}
  .toast.show{opacity:1;}

  .done-card{text-align:center; padding:36px 20px;}
  .done-card .big{font-size:38px; margin-bottom:6px;}
  .score-pills{display:flex; gap:10px; justify-content:center; flex-wrap:wrap; margin:16px 0;}
  .score-pill{padding:8px 16px; border-radius:99px; font-size:13px; font-weight:700;}

  footer.brandfoot{max-width:900px; margin:14px auto 0; padding:0 16px calc(110px + env(safe-area-inset-bottom,0px)); text-align:center; font-size:12px; color:var(--ink-soft);}

  .mode-pill{font-family:inherit; font-size:12.5px; font-weight:700; color:var(--navy); background:var(--gold); border:none; border-radius:99px; padding:6px 14px; cursor:pointer; margin-top:12px; display:inline-flex; align-items:center; gap:6px;}
  .mode-pick{display:flex; flex-direction:column; gap:14px; padding:8px 0 24px;}
  .mode-card{background:var(--card); border:1.5px solid var(--rule); border-radius:16px; padding:22px; cursor:pointer; text-align:left;}
  .mode-card:hover{border-color:var(--navy-2);}
  .mode-card .mode-icon{font-size:26px; margin-bottom:8px;}
  .mode-card h3{font-size:18px; margin-bottom:6px;}
  .mode-card p{font-size:13.5px; color:var(--ink-soft); line-height:1.5; margin:0;}
  .quiz-hint{font-size:12.5px; color:var(--ink-soft); background:var(--paper-2); border-radius:9px; padding:8px 12px; margin-bottom:14px;}
  .review-row{border:1px solid var(--rule); border-radius:10px; padding:11px 13px; margin-bottom:10px;}
  .review-tag{font-size:11.5px; font-weight:700; margin-bottom:4px; display:block;}
  .review-tag.ok{color:var(--success);} .review-tag.bad{color:var(--danger);} .review-tag.na{color:var(--ink-soft);}
  .review-q{font-size:13.5px; margin-bottom:6px; color:var(--ink-soft);}
  .review-ans{font-size:13px; margin-bottom:2px;}

  .who-row{max-width:900px; margin:12px auto 0; display:flex; flex-wrap:wrap; gap:8px; align-items:center;}
  .who-row .mode-pill{margin-top:0;}
  .who{display:inline-flex; flex-wrap:wrap; align-items:center; gap:6px; font-size:12.5px; color:#CFD7EA;}
  .who b{color:#F4EFDF;}
  .who button{font-family:inherit; font-size:12px; font-weight:700; color:#F4EFDF; background:rgba(255,255,255,.12); border:1px solid rgba(255,255,255,.22); border-radius:99px; padding:5px 11px; cursor:pointer;}
  .who button:hover{background:rgba(255,255,255,.2);}
  .login-card{max-width:460px; margin:8px auto 0; background:var(--card); border:1px solid var(--rule); border-radius:16px; padding:22px;}
  .login-card h2{font-size:21px; margin-bottom:4px;}
  .login-card p.lead{font-size:13.5px; color:var(--ink-soft); margin:0 0 16px; line-height:1.5;}
  .fld{display:flex; flex-direction:column; gap:5px; margin-bottom:12px;}
  .fld label{font-size:12px; font-weight:700; letter-spacing:.04em; text-transform:uppercase; color:var(--ink-soft);}
  .fld input{font-family:inherit; font-size:15px; padding:10px 12px; border:1.5px solid var(--rule); border-radius:9px; background:var(--paper); color:var(--ink);}
  .fld input:focus{outline:none; border-color:var(--focus); box-shadow:0 0 0 3px var(--gold-soft);}
  .fld-row{display:grid; grid-template-columns:1fr 1fr; gap:10px;}
  .login-err{font-size:13px; color:var(--danger); background:var(--danger-soft); border-radius:8px; padding:8px 10px; margin-bottom:12px;}
  .login-note{font-size:12px; color:var(--ink-soft); margin-top:12px; line-height:1.5;}
  .known{margin:0 0 16px; display:flex; flex-direction:column; gap:6px;}
  .known-label{font-size:12px; font-weight:700; letter-spacing:.04em; text-transform:uppercase; color:var(--ink-soft);}
  .known-btn{display:flex; justify-content:space-between; align-items:center; gap:10px; text-align:left; font-family:inherit; font-size:14.5px; padding:10px 12px; border:1.5px solid var(--rule); border-radius:10px; background:var(--paper); color:var(--ink); cursor:pointer;}
  .known-btn:hover{border-color:var(--navy-2);}
  .known-btn small{font-size:12px; color:var(--ink-soft);}
  .rec-card{background:var(--card); border:1px solid var(--rule); border-radius:14px; padding:18px; margin-bottom:14px;}
  .rec-card h2{font-size:19px; margin-bottom:10px;}
  .rec-card h3{font-size:15px; margin:4px 0 8px;}
  .rec-table-wrap{overflow-x:auto;}
  .rec-table{width:100%; border-collapse:collapse; font-size:13.5px; font-variant-numeric:tabular-nums;}
  .rec-table th{text-align:left; font-size:11.5px; text-transform:uppercase; letter-spacing:.04em; color:var(--ink-soft); padding:6px 8px; border-bottom:1px solid var(--rule); white-space:nowrap;}
  .rec-table td{padding:8px; border-bottom:1px solid var(--rule); white-space:nowrap;}
  .rec-bar{display:inline-block; width:70px; height:6px; border-radius:99px; background:var(--rule); overflow:hidden; vertical-align:middle; margin-right:6px;}
  .rec-bar i{display:block; height:100%; background:var(--success);}
  .rec-empty{font-size:13.5px; color:var(--ink-soft);}
  .sec-sub{max-width:900px; margin:0 auto; padding:10px 16px 0; font-size:12.5px; font-weight:700; color:var(--accent-text); letter-spacing:.02em;}
  .opt{flex-wrap:wrap;}
  .opt-l{font-family:'IBM Plex Mono',monospace; font-size:13px; font-weight:600; color:var(--ink-soft);}
  .opt-t{flex:1; min-width:0;}
  .opt.is-chosen:not(.is-correct):not(.is-wrong){border-color:var(--navy-2); background:var(--gold-soft);}
  .opt-tag{font-size:11px; font-weight:700; padding:2px 8px; border-radius:99px; background:var(--card); border:1px solid currentColor; white-space:nowrap;}
  .opt.is-correct .opt-tag{color:var(--success);} .opt.is-wrong .opt-tag{color:var(--danger);} .opt.is-chosen:not(.is-correct):not(.is-wrong) .opt-tag{color:var(--accent-text);}
  .chosen{font-size:13.5px; margin-top:10px; padding:8px 12px; border-radius:9px;}
  .chosen.ok{background:var(--success-soft); color:var(--success);} .chosen.bad{background:var(--danger-soft); color:var(--danger);}
  .chosen + .chosen{margin-top:6px;}
  .solution{margin-top:14px; border:1px solid var(--rule); border-left:4px solid var(--gold); background:var(--paper-2); border-radius:10px; padding:12px 14px;}
  .sol-h{font-family:'Fraunces',Georgia,serif; font-weight:700; font-size:14px; color:var(--accent-text); margin-bottom:6px;}
  .sol-line{font-size:14.5px; line-height:1.7;}
  .rev-sol summary{cursor:pointer; font-size:12.5px; font-weight:700; color:var(--accent-text); margin-top:6px;}
  .rev-sol .solution{margin-top:8px;}
  .chapter-credit{max-width:900px; margin:4px auto 0; font-size:12px; color:#CFD7EA;}
  footer.brandfoot a{color:inherit;}
  .blank-input.wide{width:260px; max-width:100%; font-family:'Source Sans 3',sans-serif;}
  .blank-input.expr{width:170px; max-width:100%;}
  /*fix-layout*/ .cp-fill,.sp-fill{width:0;} .fld{min-width:0;} .fld input{width:100%; min-width:0; box-sizing:border-box;}
  .fig{margin:6px 0 10px; display:flex; justify-content:center;}
  .figsvg{width:100%; max-width:340px; height:auto; overflow:visible;}
  .figsvg .ln,.figsvg .arm{stroke:var(--ink); stroke-width:1.6; fill:none;}
  .figsvg .arm{stroke:var(--accent-text); stroke-width:2;}
  .figsvg .pt{fill:var(--ink);}
  .figsvg .lb{fill:var(--ink); font:600 13px 'Source Sans 3',sans-serif;}
  .figsvg .al{fill:var(--accent-text); font:700 12px 'Source Sans 3',sans-serif;}
  .figsvg .wg{fill:var(--gold-soft); stroke:var(--gold); stroke-width:1.2;}
  .figsvg .wg2{fill:rgba(199,154,62,.35); stroke:var(--gold); stroke-width:1.2;}
  .figsvg .ra{fill:none; stroke:var(--ink); stroke-width:1.2;}
  .figsvg .ahd{fill:var(--ink);}
  .figsvg .pr{fill:var(--paper-2); stroke:var(--ink-soft); stroke-width:1.2;}
  .figsvg .tk{stroke:var(--ink-soft); stroke-width:.8;}
  .figsvg .po{fill:var(--ink); font:600 8.5px 'IBM Plex Mono',monospace;}
  .figsvg .pi{fill:var(--danger); font:600 7.5px 'IBM Plex Mono',monospace;}
  .figsvg .sh{fill:var(--gold-soft); stroke:var(--ink); stroke-width:1.5; stroke-linejoin:round;}
  .figsvg .sh2{fill:rgba(199,154,62,.38); stroke:var(--ink); stroke-width:1.5; stroke-linejoin:round;}
  .figsvg .sh3{fill:rgba(199,154,62,.22); stroke:var(--ink); stroke-width:1.5; stroke-linejoin:round;}
  .figsvg .none{fill:none;}
  .figsvg .hid{stroke-dasharray:5 4; fill:none;}
  .figsvg .tick{stroke:var(--ink); stroke-width:1.4; fill:none;}
  .figsvg .shd{fill:var(--accent-text); fill-opacity:.55;}
  .figsvg .cell{fill:var(--card); stroke:var(--ink); stroke-width:1.1;}
  .figsvg .dr{fill:var(--danger);} .figsvg .dw{fill:var(--card); stroke:var(--ink); stroke-width:1.2;}
  .figsvg .dotfill{fill:var(--danger);}
  .tt{border-collapse:collapse; font-size:13.5px; margin:4px auto; font-variant-numeric:tabular-nums;} .tt th,.tt td{border:1px solid var(--rule); padding:4px 9px; text-align:left;} .tt th{background:var(--paper-2); font-weight:700;} .ttw{overflow-x:auto; max-width:100%;}
  .fq{display:inline-flex; flex-direction:column; vertical-align:middle; text-align:center; font-size:.82em; line-height:1.12; margin:0 2px;}
  .fq>span:first-child{border-bottom:1.5px solid currentColor; padding:0 2px;}
  .fq>span:last-child{padding:0 2px;}
  .mx{white-space:nowrap;}
  .blank-input.fr{width:110px;}
  @media (prefers-reduced-motion:reduce){ *{transition:none !important;} }
.datline{display:block;margin-top:8px;padding:8px 10px;border-radius:8px;background:var(--paper-2);font:500 14px/1.7 'IBM Plex Mono',monospace;word-spacing:2px;overflow-wrap:anywhere;}

  .theory{display:flex;flex-direction:column;gap:16px;padding-bottom:40px;}
  .hub{display:grid;grid-template-columns:1fr;gap:12px;}
  @media (min-width:640px){ .hub{grid-template-columns:repeat(3,1fr);} }
  .hub-card{background:var(--card);border:1px solid var(--rule);border-radius:14px;padding:16px;display:flex;flex-direction:column;gap:8px;}
  .hub-card h3{font-family:'Fraunces',serif;font-size:18px;margin:0;color:var(--accent-text);}
  .hub-card p{margin:0;font-size:14px;color:var(--ink-soft);line-height:1.5;}
  .hub-btns{display:flex;flex-wrap:wrap;gap:8px;margin-top:auto;}
  .hub-btn{min-height:40px;border:1.5px solid var(--rule);background:var(--paper-2);color:var(--ink);border-radius:10px;padding:8px 12px;font:600 14px 'Source Sans 3',sans-serif;cursor:pointer;text-align:left;}
  .hub-btn:hover{border-color:var(--gold);}
  .hub-btn.primary{background:var(--navy);color:#F4EFDF;border-color:var(--navy);}
  .note{background:var(--card);border:1px solid var(--rule);border-radius:14px;padding:18px;scroll-margin-top:120px;}
  .note h2{font-family:'Fraunces',serif;font-size:22px;margin:0 0 4px;color:var(--ink);}
  .note .lt{font-size:13.5px;color:var(--ink-soft);margin:0 0 12px;}
  .note .lt b{color:var(--accent-text);}
  .note h4{font:700 15px 'Source Sans 3',sans-serif;margin:16px 0 6px;color:var(--accent-text);}
  .note p,.note li{font-size:15.5px;line-height:1.6;}
  .note ul{padding-left:20px;margin:6px 0;}
  .keybox{background:var(--gold-soft);border-left:4px solid var(--gold);border-radius:8px;padding:10px 12px;margin:10px 0;font-size:15px;line-height:1.6;}
  .keybox b{color:var(--ink);}
  .ex{background:var(--paper-2);border-radius:10px;padding:12px;margin:10px 0;}
  .ex .exh{font-family:'Fraunces',serif;font-weight:700;color:var(--accent-text);margin-bottom:4px;}
  .ex .exl{font-size:15px;line-height:1.7;}
  .ttab{width:100%;border-collapse:collapse;font-size:14.5px;margin:8px 0;}
  .ttab th,.ttab td{border:1px solid var(--rule);padding:7px 8px;text-align:left;vertical-align:top;}
  .ttab th{background:var(--paper-2);}
  .tscroll{overflow-x:auto;}
  .mono{font-family:'IBM Plex Mono',monospace;font-size:.92em;}
  @media (max-width:480px){ .ttab{font-size:13.5px;} .ttab th,.ttab td{padding:6px;} }
  .note .figsvg{max-width:100%;height:auto;display:block;margin:8px auto;}


  .rep-top{display:flex;flex-wrap:wrap;gap:18px;align-items:center;justify-content:center;margin-top:8px;}
  .rep-legend{flex:1;min-width:220px;display:flex;flex-direction:column;gap:8px;}
  .rep-cap{font:700 13px 'Source Sans 3',sans-serif;color:var(--ink-soft);text-transform:uppercase;letter-spacing:.05em;}
  .rep-li{display:flex;align-items:center;gap:6px;font-size:15px;}
  .rep-n{margin-left:auto;white-space:nowrap;padding-left:8px;font-family:'IBM Plex Mono',monospace;font-weight:600;}
  .sw{display:inline-block;width:12px;height:12px;border-radius:3px;flex:none;}
  .rep-grid{display:grid;grid-template-columns:1fr;gap:12px;}
  @media (min-width:640px){ .rep-grid{grid-template-columns:1fr 1fr;} }
  .rep-card{background:var(--card);border:1px solid var(--rule);border-radius:14px;padding:14px;display:flex;flex-direction:column;gap:10px;}
  .rep-h{display:flex;align-items:center;gap:8px;font:700 16px 'Source Sans 3',sans-serif;}
  .crit{display:inline-grid;place-items:center;width:28px;height:28px;border-radius:50%;color:var(--card);font:700 15px Fraunces,serif;flex:none;}
  .rep-row{display:flex;gap:14px;align-items:center;}
  .rep-stats{display:flex;flex-direction:column;gap:5px;font-size:14.5px;}
  .rep-stats div{display:flex;align-items:center;gap:6px;}
  .rep-lvl{margin-top:4px;color:var(--accent-text);} .rep-lvl span{color:var(--ink-soft);font-size:13px;}
  .rep-note{font-size:13px;color:var(--ink-soft);}


  .skip-chips{display:flex;flex-wrap:wrap;gap:8px;justify-content:center;margin:12px 0;}
  .skip-chips .chip{min-width:48px;min-height:40px;cursor:pointer;border:1.5px solid var(--gold);background:var(--gold-soft);color:var(--retry-text);border-radius:10px;font:600 14px 'IBM Plex Mono',monospace;}
  .skip-btns{display:flex;flex-wrap:wrap;gap:10px;justify-content:center;margin-top:12px;}


  .kb-toggle{border:none;background:transparent;font-size:15px;cursor:pointer;padding:0 2px;vertical-align:middle;opacity:.7;}
  .vkb{position:fixed;left:0;right:0;bottom:0;z-index:80;background:var(--paper-2);border-top:1px solid var(--rule);box-shadow:0 -6px 20px rgba(0,0,0,.12);padding:6px 6px 8px;display:none;}
  .vkb.show{display:block;}
  .vkb-top{display:flex;justify-content:space-between;align-items:center;max-width:640px;margin:0 auto 4px;font:600 12px 'Source Sans 3',sans-serif;color:var(--ink-soft);}
  .vkb-link{border:none;background:none;color:var(--accent-text);font:600 12px 'Source Sans 3',sans-serif;cursor:pointer;text-decoration:underline;}
  .vkb-row{display:flex;gap:5px;max-width:640px;margin:0 auto 5px;}
  .vkb-k{flex:1;min-height:42px;border:1px solid var(--rule);border-radius:8px;background:var(--card);color:var(--ink);font:600 17px 'IBM Plex Mono',monospace;cursor:pointer;padding:0;}
  .vkb-k.fn{font:600 13px 'Source Sans 3',sans-serif;background:var(--gold-soft);}
  .vkb-k.done{background:var(--navy);color:#F4EFDF;border-color:var(--navy);}
  .vkb-k:active{transform:scale(.96);}
  body.kb-open .wrap{padding-bottom:360px;}
  body.kb-open .fab{display:none;}
  .tool-bar{display:flex;gap:8px;flex-wrap:wrap;margin:-4px 0 10px;}
  .tool-btn{min-height:36px;border:1.5px solid var(--gold);background:var(--gold-soft);color:var(--ink);border-radius:18px;padding:4px 12px;font:600 13.5px 'Source Sans 3',sans-serif;cursor:pointer;}
  .tool-panel{position:fixed;z-index:85;background:var(--card);border:1px solid var(--rule);border-radius:14px;box-shadow:0 10px 30px rgba(0,0,0,.25);display:none;}
  .tool-panel.show{display:block;}
  .tp-head{display:flex;align-items:center;gap:8px;padding:8px 10px;border-bottom:1px solid var(--rule);font:600 14px 'Source Sans 3',sans-serif;}
  .tp-note{font-size:12px;color:var(--ink-soft);font-weight:500;}
  .tp-x{margin-left:auto;border:1px solid var(--rule);background:var(--paper-2);color:var(--ink);border-radius:8px;min-height:32px;padding:2px 10px;cursor:pointer;font:600 13px 'Source Sans 3',sans-serif;}
  .tp-x + .tp-x{margin-left:0;}
  .calc{right:12px;bottom:84px;width:min(330px,calc(100vw - 24px));}
  body.calc-open .wrap{padding-bottom:440px;}
  body.calc-open .fab{display:none;}
  @media (max-width:640px){ .calc{left:6px;right:6px;width:auto;} .calc-keys button{min-height:36px;} }
  .calc-disp{padding:8px 12px;text-align:right;background:var(--paper-2);}
  .calc-expr{font:500 13px 'IBM Plex Mono',monospace;color:var(--ink-soft);min-height:18px;word-break:break-all;}
  .calc-res{font:600 24px 'IBM Plex Mono',monospace;color:var(--ink);word-break:break-all;}
  .calc-keys{display:grid;grid-template-columns:repeat(6,1fr);gap:5px;padding:8px;}
  .calc-keys button{min-height:40px;border:1px solid var(--rule);border-radius:8px;background:var(--card);color:var(--ink);font:600 14px 'IBM Plex Mono',monospace;cursor:pointer;padding:0;}
  .calc-keys button.fn{background:var(--gold-soft);font-family:'Source Sans 3',sans-serif;font-size:13px;}
  .calc-keys button.eq{grid-column:span 2;background:var(--navy);color:#F4EFDF;border-color:var(--navy);}
  .desmos{left:50%;top:50%;transform:translate(-50%,-50%);width:min(760px,calc(100vw - 16px));height:min(560px,calc(100vh - 90px));flex-direction:column;}
  .desmos.show{display:flex;}
  #desmosBox{flex:1;min-height:0;border-radius:0 0 14px 14px;overflow:hidden;}
  .desmos-msg{padding:24px;text-align:center;color:var(--ink-soft);}
  .chip[data-status="skipped"]{cursor:pointer;}
  .chip[data-status="answered"]{border-color:var(--accent-text);color:var(--accent-text);}


  button.crest-home{border:none;padding:0;position:relative;cursor:pointer;transition:transform .15s ease;}
  button.crest-home:hover,button.crest-home:focus-visible{transform:scale(1.06);outline:2px solid var(--gold);outline-offset:2px;}
  .crest-h{position:absolute;right:-7px;bottom:-7px;width:18px;height:18px;border-radius:50%;background:#F4EFDF;color:var(--navy);font:700 12px/18px 'Source Sans 3',sans-serif;text-align:center;box-shadow:0 1px 3px rgba(0,0,0,.3);}
  .brand .brand-row{position:relative;}
  .bmasw{position:absolute;left:50%;top:50%;transform:translate(-50%,-50%);display:flex;flex-shrink:0;white-space:nowrap;align-items:center;gap:6px;background:rgba(255,255,255,.12);border:1px solid rgba(255,255,255,.25);border-radius:99px;padding:5px 14px;color:#F4EFDF;}
  .bmasw-ic{font-size:16px;} .bmasw-t{font:600 20px 'IBM Plex Mono',monospace;letter-spacing:.02em;min-width:62px;text-align:center;}
  .bmasw-b{border:none;background:rgba(255,255,255,.18);color:#F4EFDF;border-radius:50%;width:30px;height:30px;cursor:pointer;font-size:13px;}
  .bmasw.off{display:none;}
  @media (max-width:560px){ .bmasw{position:static;transform:none;margin-left:auto;padding:4px 5px 4px 8px;gap:4px;} .bmasw-ic{display:none;} .bmasw-t{font-size:16px;min-width:48px;} .bmasw-b{width:26px;height:26px;} .brand .series-name{font-size:15px;} .brand .brand-name{font-size:10.5px;} .brand .brand-row>div:not(.bmasw){min-width:0;} }
  .bmasw-done{font:600 15px 'IBM Plex Mono',monospace;color:var(--accent-text);margin:4px 0 8px;}
  .sp-fab{position:fixed;left:14px;bottom:84px;z-index:60;border:1.5px solid var(--navy-2);background:var(--card);color:var(--ink);border-radius:99px;padding:9px 14px;font:700 14px 'Source Sans 3',sans-serif;box-shadow:0 4px 14px rgba(0,0,0,.15);cursor:pointer;}
  .sp-fab.on{background:var(--navy);color:#F4EFDF;}
  body.kb-open .sp-fab{display:none;}
  .sp-canvas{position:absolute;z-index:55;display:none;touch-action:none;cursor:crosshair;}
  .sp-canvas.passive{pointer-events:none;cursor:default;}
  .sp-bar{position:fixed;top:8px;left:8px;right:8px;margin:0 auto;width:max-content;z-index:90;display:none;align-items:center;gap:6px;background:var(--card);border:1px solid var(--rule);border-radius:14px;padding:6px 8px;box-shadow:0 6px 20px rgba(0,0,0,.2);max-width:calc(100vw - 16px);flex-wrap:wrap;justify-content:center;}
  .sp-lbl{font:700 13px 'Source Sans 3',sans-serif;color:var(--ink-soft);margin-right:2px;}
  .sp-pen,.sp-tool{width:38px;height:38px;border-radius:10px;border:1.5px solid var(--rule);background:var(--paper);cursor:pointer;display:inline-flex;align-items:center;justify-content:center;font-size:17px;padding:0;color:var(--ink);}
  .sp-pen i{width:20px;height:20px;border-radius:50%;display:block;}
  .sp-pen.on,.sp-tool.on{border-color:var(--navy-2);box-shadow:0 0 0 3px var(--gold-soft);}
  @media (max-width:560px){ .sp-lbl{display:none;} .sp-pen,.sp-tool{width:34px;height:34px;} .sp-fab span{display:none;} }

  /* larger reading sizes */
  .chapter-eyebrow{font-size:13.5px;}
  .chapter-title{font-size:36px;line-height:1.15;}
  .chapter-sub{font-size:16.5px;}
  .tab-btn{font-size:15.5px;}
  .sec-sub{font-size:15px;}
  .qtext{font-size:19px;line-height:1.55;}
  .qnum{width:36px;height:36px;font-size:16px;}
  .opt{font-size:17.5px;padding:12px 14px;}
  .step-line{font-size:17.5px;line-height:2;}
  .blank-input{font-size:16px;}
  .sol-line{font-size:16.5px;}
  .feedback{font-size:15px;}
  .note h2{font-size:28px;}
  .note h4{font-size:19px;}
  .note p,.note li{font-size:17.5px;line-height:1.65;}
  .note .lt{font-size:15.5px;}
  .ex .exh{font-size:18px;} .ex .exl{font-size:16.5px;}
  .keybox{font-size:16.5px;}
  .ttab{font-size:15.5px;}
  .hub-card h3{font-size:21px;} .hub-card p{font-size:15.5px;} .hub-btn{font-size:15px;}
  @media (max-width:480px){ .chapter-title{font-size:30px;} .qtext{font-size:18px;} .opt,.step-line{font-size:16.5px;} .note h2{font-size:24px;} .note p,.note li{font-size:16.5px;} }
</style>
</head>
<body>
<header class="brand">
  <div class="brand-row">
    <div class="crest">BM</div>
    <div>
      <div class="brand-name">Brain &amp; Mind Academy</div>
      <div class="series-name">Sopaan <span style="font-weight:400;font-size:14px;color:#CFD7EA;">Practice Series</span></div>
    </div>
  </div>
  <div class="chapter-eyebrow">Class 8 Mathematics · Chapter 12</div>
  <div class="chapter-title">Direct and Inverse Variations</div>
  <div class="chapter-sub">Theory Notes · Practice by Learning Objective · Learning Assessment</div><div class="chapter-credit">Mixed multiple-choice and fill-in-the-blank practice · Chapter 12</div>
  <div class="chapter-progress">
    <div class="cp-track"><div class="cp-fill" id="cpFill"></div></div>
    <div class="cp-label" id="cpLabel">0% complete</div>
  </div>
  <div class="who-row"><button class="mode-pill" id="modePill" hidden>Choose a mode</button><span class="who" id="whoBar" hidden></span></div>
</header>

<nav class="tabbar"><div class="tabbar-inner" id="tabbar"></div></nav>
<div class="sec-sub" id="secSub"></div><div class="slide-progress"><div class="sp-track"><div class="sp-fill" id="spFill"></div></div><div class="sp-label" id="spLabel">Question 1 of 49</div></div>
<div class="wrap" id="wrap"></div>
<footer class="brandfoot">Brain &amp; Mind Academy · Sopaan Practice Series · Class 8 Mathematics · Chapter 12<br>Chapter follows the Class 8 mathematics syllabus (New Enjoying Mathematics, Class 8). Theory notes, questions, learning assessments and worked solutions are written by Brain &amp; Mind Academy.</footer>

<div class="navbar"><div class="navbar-inner" id="navbarInner"></div></div>
<button class="fab" id="paletteFab"><span>Questions</span><span class="fab-badge" id="fabBadge">0/49</span></button>

<div class="overlay" id="overlay">
  <div class="palette" role="dialog" aria-label="Question palette">
    <div class="palette-head"><h2 id="paletteTitle">Question palette</h2><button class="palette-close" id="paletteClose">&times;</button></div>
    <div class="palette-legend">
      <span><i class="dot current"></i>Current</span><span><i class="dot correct"></i>Correct</span>
      <span><i class="dot revealed"></i>Revealed</span><span><i class="dot skipped"></i>Skipped</span>
      <span><i class="dot locked"></i>Locked</span>
    </div>
    <div class="chip-grid" id="paletteBody"></div>
  </div>
</div>
<div class="toast" id="toast"></div>

<script>
(function(){
"use strict";

/* ================= audio ================= */
var audioCtx=null;
function ensureAudio(){ if(!audioCtx){ try{ audioCtx=new (window.AudioContext||window.webkitAudioContext)(); }catch(e){} } return audioCtx; }
function playTone(freqs,dur,type){
  var ctx=ensureAudio(); if(!ctx) return;
  try{
    var t0=ctx.currentTime;
    freqs.forEach(function(f,i){
      var o=ctx.createOscillator(), g=ctx.createGain();
      o.type=type||'sine'; o.frequency.value=f;
      var start=t0+i*dur;
      g.gain.setValueAtTime(0.0001,start);
      g.gain.exponentialRampToValueAtTime(0.16,start+0.02);
      g.gain.exponentialRampToValueAtTime(0.0001,start+dur);
      o.connect(g); g.connect(ctx.destination);
      o.start(start); o.stop(start+dur+0.02);
    });
  }catch(e){}
}
function playSuccess(){ playTone([523.25,659.25,783.99],0.11,'sine'); }
function playWrong(){ playTone([220,185],0.14,'square'); }
function playReveal(){ playTone([300,220],0.16,'triangle'); }

/* ================= helpers ================= */
function norm(s){
  return String(s===undefined||s===null?'':s).trim().toLowerCase().replace(/\s+/g,'')
    .replace(/[×∗*·]/g,'x').replace(/÷/g,'/').replace(/–|—|−/g,'-')
    .replace(/[²]/g,'^2').replace(/[³]/g,'^3').replace(/[⁴]/g,'^4').replace(/[⁵]/g,'^5')
    .replace(/[⁶]/g,'^6').replace(/[⁷]/g,'^7').replace(/[⁸]/g,'^8').replace(/[⁹]/g,'^9')
    .replace(/\^/g,'');
}
function parseNum(s){
  if(s===undefined||s===null) return null;
  var t=String(s).trim().replace(/,/g,'').replace(/[−–—]/g,'-').replace(/\s+/g,''); if(t==='') return null;
  var neg=false; if(t[0]==='-'){neg=true;t=t.slice(1);}
  var m=t.match(/^(\d+)\/(\d+)$/);
  if(m){ var v=parseInt(m[1],10)/parseInt(m[2],10); return neg?-v:v; }
  if(/^\d+(\.\d+)?$/.test(t)){ var v2=parseFloat(t); return neg?-v2:v2; }
  return null;
}
/* ---- expression checker: compares answers like (P-2w)/2 and P/2-w at random values ---- */
function exprPrep(s){
  return String(s).toLowerCase().replace(/\s+/g,'').replace(/^[a-z]\(x\)=/i,'').replace(/^y=/i,'').replace(/[×∗·]/g,'*').replace(/÷/g,'/').replace(/[−–—]/g,'-')
    .replace(/²/g,'^2').replace(/³/g,'^3').replace(/⁴/g,'^4').replace(/⁵/g,'^5').replace(/⁶/g,'^6').replace(/⁷/g,'^7').replace(/⁸/g,'^8').replace(/⁹/g,'^9').replace(/π/g,'#').replace(/pi/gi,'#').replace(/½/g,'(1/2)');
}
function exprCompile(src){
  var s=exprPrep(src), i=0, toks=[], absDepth=0;
  while(i<s.length){
    var ch=s[i];
    if(/[0-9.]/.test(ch)){ var j=i; while(j<s.length && /[0-9.]/.test(s[j])) j++; toks.push({k:'n',v:parseFloat(s.slice(i,j))}); i=j; continue; }
    if(/[a-zA-Z#]/.test(ch)){ toks.push({k:'v',v:ch}); i++; continue; }
    if(ch==='|'){ var pv=toks[toks.length-1]; var opn=(absDepth===0)||!pv||('+-*/^(['.indexOf(pv.k)>=0); if(opn){ absDepth++; toks.push({k:'['}); } else { absDepth--; toks.push({k:']'}); } i++; continue; }
    if('+-*/^()'.indexOf(ch)>=0){ toks.push({k:ch}); i++; continue; }
    return null;
  }
  var out=[];
  for(var t=0;t<toks.length;t++){
    var a=toks[t], b=out[out.length-1];
    if(b && (b.k==='n'||b.k==='v'||b.k===')'||b.k===']') && (a.k==='n'||a.k==='v'||a.k==='('||a.k==='[')) out.push({k:'&'});
    out.push(a);
  }
  var p=0;
  function peek(){ return out[p]; }
  function parseE(){ var n=parseT(); while(peek() && (peek().k==='+'||peek().k==='-')){ var o=out[p++].k, r=parseT(); n=(function(l,r,o){return function(e){ return o==='+'?l(e)+r(e):l(e)-r(e); };})(n,r,o); } return n; }
  function parseI(){ var n=parseU(); while(peek() && peek().k==='&'){ p++; var r=parseP(); n=(function(l,r){return function(e){ return l(e)*r(e); };})(n,r); } return n; }
  function parseT(){ var n=parseI(); while(peek() && (peek().k==='*'||peek().k==='/')){ var o=out[p++].k, r=parseI(); n=(function(l,r,o){return function(e){ return o==='*'?l(e)*r(e):l(e)/r(e); };})(n,r,o); } return n; }
  function parseU(){ if(peek() && peek().k==='-'){ p++; var u=parseU(); return function(e){ return -u(e); }; } if(peek() && peek().k==='+'){ p++; return parseU(); } return parseP(); }
  function parseP(){ var b=parseA(); if(peek() && peek().k==='^'){ p++; var x=parseU(); return function(e){ return Math.pow(b(e),x(e)); }; } return b; }
  function parseA(){
    var t=out[p++]; if(!t) throw 0;
    if(t.k==='n') return function(){ return t.v; };
    if(t.k==='v') return t.v==='#' ? function(){ return Math.PI; } : function(e){ return e[t.v]; };
    if(t.k==='('){ var n=parseE(); if(!peek()||peek().k!==')') throw 0; p++; return n; }
    if(t.k==='['){ var m=parseE(); if(!peek()||peek().k!==']') throw 0; p++; return function(e){ return Math.abs(m(e)); }; }
    throw 0;
  }
  try{ var f=parseE(); if(p!==out.length) return null; return f; }catch(e){ return null; }
}
function exprEqual(input,answer){
  var f=exprCompile(input), g=exprCompile(answer); if(!f||!g) return false;
  var hits=0;
  for(var trial=0;trial<8;trial++){
    var env={}; 'abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ'.split('').forEach(function(c){ env[c]=1.3+Math.random()*4.1; });
    var x=f(env), y=g(env);
    if(!isFinite(x)||!isFinite(y)) continue;
    if(Math.abs(x-y)>1e-7*Math.max(1,Math.abs(x),Math.abs(y))) return false;
    hits++;
  }
  return hits>=3;
}
function wordsNorm(s){ return String(s||'').toLowerCase().replace(/\band\b/g,' ').replace(/[^a-z]/g,''); }
function listNorm(s){ return (String(s||'').replace(/[−–—]/g,'-').replace(/(\d) (?=\d{3}\b)/g,'$1').match(/-?\d+(\.\d+)?/g)||[]).join(','); }
function powNorm(s){ return String(s||'').toLowerCase().replace(/\s+/g,'').replace(/[×∗*·.]/g,'x').replace(/[⁰¹²³⁴⁵⁶⁷⁸⁹]+/g,function(m){ return '^'+m.split('').map(function(c){ return '⁰¹²³⁴⁵⁶⁷⁸⁹'.indexOf(c); }).join(''); }).replace(/\^1(?!\d)/g,''); }
function fr(s){ return String(s).replace(/\{(\d+) (\d+)\/(\d+)\}/g,'<span class="mx">$1<span class="fq"><span>$2</span><span>$3</span></span></span>').replace(/\{(\d+)\/(\d+)\}/g,'<span class="fq"><span>$1</span><span>$2</span></span>'); }
function gcdI(a,b){ a=Math.abs(a); b=Math.abs(b); while(b){ var t=a%b; a=b; b=t; } return a; }
function fracParse(s){ s=String(s===undefined||s===null?'':s).trim().replace(/[\u2044\u2215\u00f7]/g,'/').replace(/\s+/g,' ').replace(/\s*\/\s*/g,'/'); var m;
  if((m=s.match(/^(-?\d+)$/))) return {v:+m[1],form:'int',n:+m[1],d:1};
  if((m=s.match(/^(-?\d+)\/(\d+)$/))){ if(+m[2]===0) return null; return {v:m[1]/m[2],form:'frac',n:+m[1],d:+m[2]}; }
  if((m=s.match(/^(-?)(\d+)(?: |\+)(\d+)\/(\d+)$/))){ if(+m[4]===0) return null; var sg=m[1]?-1:1; return {v:sg*(+m[2]+m[3]/m[4]),form:'mixed',w:sg*m[2],n:+m[3],d:+m[4]}; }
  if((m=s.match(/^-?\d*\.\d+$/))) return {v:parseFloat(s),form:'dec'};
  return null; }
function fracOK(mode,input,answer){
  if(mode==='flist'){ var A=String(input).split(/[,;]/).map(function(x){return x.trim();}).filter(Boolean), K=String(answer).split(/[,;]/).map(function(x){return x.trim();});
    if(A.length!==K.length) return false; return A.every(function(x,i){ var a=fracParse(x), k=fracParse(K[i]); return a&&k&&Math.abs(a.v-k.v)<1e-9; }); }
  var a=fracParse(input), k=fracParse(answer); if(!a||!k) return false;
  var same=Math.abs(a.v-k.v)<1e-9; if(!same) return false;
  if(mode==='fv') return true;
  if(mode==='dec') return a.form==='dec'||a.form==='int';
  if(mode==='fe') return (a.form==='frac'&&k.form==='frac'&&a.n===k.n&&a.d===k.d)||(a.form==='int'&&k.form==='int');
  if(mode==='fi') return a.form==='frac'||(a.form==='int'&&k.form==='int');
  if(mode==='fl') return a.form==='int'||(a.form==='frac'&&gcdI(a.n,a.d)===1)||(a.form==='mixed'&&a.n<a.d&&gcdI(a.n,a.d)===1);
  if(mode==='fm') return a.form==='int'||(a.form==='mixed'&&a.n>0&&a.n<a.d&&gcdI(a.n,a.d)===1);
  return false; }
function answerMatches(input,answer,accept,expr){
  if(expr==='dec'||expr==='fv'||expr==='fe'||expr==='fl'||expr==='fm'||expr==='fi'||expr==='flist'){ if(input===undefined||input===null||String(input).trim()==='') return false; return fracOK(expr,input,answer); }
  if(input===undefined||input===null||String(input).trim()==='') return false;
  if(expr==='words'){ return [answer].concat(accept||[]).some(function(a){ if(/\d/.test(a)) return norm(a)===norm(input); var w=wordsNorm(a); return w!=='' && w===wordsNorm(input); }); }
  if(expr==='list'){ return [answer].concat(accept||[]).some(function(a){ return listNorm(a)===listNorm(input); }); }
  if(expr==='pow'){ return [answer].concat(accept||[]).some(function(a){ return powNorm(a)===powNorm(input); }); }
  if(expr==='time'){ var tn=function(x){ var t=String(x).toLowerCase().replace(/[\s.]/g,'').replace(/[:h]/g,''); if(/^\d{3}(am|pm)?$/.test(t)) t='0'+t; return t; }; return [answer].concat(accept||[]).some(function(a){ return tn(a)===tn(input); }); }
  if(expr==='glist'){ var gn=function(x){ return String(x).toUpperCase().split(/[\s,;]+/).filter(Boolean).sort().join(','); }; return [answer].concat(accept||[]).some(function(a){ return gn(a)===gn(input); }); }
  if(expr==='coord'){ var cn=function(x){ return String(x).replace(/[\u2212\u2013\u2014]/g,'-').replace(/[\s()\[\]]/g,''); }; return [answer].concat(accept||[]).some(function(a){ return cn(a)===cn(input); }); }
  if(expr==='dlist'){ var dn=function(x){ return (String(x).replace(/[−–—]/g,'-').match(/-?\d*\.?\d+/g)||[]).map(Number).join(','); }; return [answer].concat(accept||[]).some(function(a){ return dn(a)===dn(input); }); }
  if(expr==='set'){ var sn=function(x){ return (String(x).match(/-?\d+/g)||[]).map(Number).sort(function(a,b){return a-b;}).join(','); }; return [answer].concat(accept||[]).some(function(a){ return sn(a)===sn(input); }); }
  if(expr==='primes'){ var pn=function(x){ var t=powNorm(x).replace(/[^0-9x^]/g,''); var out=[]; t.split('x').forEach(function(tok){ if(!tok) return; var m=tok.split('^'); var b=+m[0], e=m[1]?+m[1]:1; for(var i=0;i<e;i++) out.push(b); }); return out.sort(function(a,b){return a-b;}).join(','); }; return [answer].concat(accept||[]).some(function(a){ return pn(a)===pn(input); }); }
  if(expr==='angle'){ var an=function(x){ return String(x).toUpperCase().replace(/[^A-Z]/g,''); }; var k=an(answer), v=an(input); return v===k || v===k.split('').reverse().join(''); }
  if(expr==='trans'){ var tv=function(x){ var s=String(x).toLowerCase().replace(/[−–—]/g,'-').replace(/\b(units?|squares?|and|then|steps?|to|the|a)\b/g,' ').replace(/[,;.]/g,' '); var re=/(\d+)\s*(right|left|up|down|r|l|u|d)\b/g, m, dx=0, dy=0, n=0; while((m=re.exec(s))){ var v=+m[1], d=m[2][0]; if(d==='r')dx+=v; else if(d==='l')dx-=v; else if(d==='u')dy+=v; else dy-=v; n++; } if(!n||s.replace(re,'').replace(/\s+/g,'')!=='') return null; return dx+','+dy; }; var ti=tv(input); return ti!==null && [answer].concat(accept||[]).some(function(a){ return tv(a)===ti; }); }
  if(expr==='rot'){ var rv=function(x){ var s=String(x).toLowerCase().replace(/quarter[\s-]*turn/g,'90').replace(/half[\s-]*turn/g,'180').replace(/three[\s-]*quarter[\s-]*turn/g,'270'); var m=s.match(/\b(90|180|270)\b/); if(!m) return null; var a=+m[1]; if(a===180) return '180'; var dir=/anti|counter|acw|ccw/.test(s)?-1:(/clockwise|\bcw\b/.test(s)?1:0); if(!dir) return null; return String(((a*dir)%360+360)%360); }; var ri=rv(input); return ri!==null && ri===rv(answer); }
  if(expr==='expanded'){ var f=function(x){ return String(x).replace(/\s+/g,'').replace(/,/g,''); }; return [answer].concat(accept||[]).some(function(a){ return f(a)===f(input); }); }
  if(expr===true && input!==undefined && input!==null && String(input).trim()!==''){
    if(exprEqual(input,answer)) return true;
    var alt=String(input).replace(/\/\s*(\d+(?:\.\d+)?)\s*([a-zA-Z(])/g,'/$1*$2'); if(alt!==String(input) && exprEqual(alt,answer)) return true;
    return (accept||[]).some(function(a){ return exprEqual(input,a); });
  }
  if(input===undefined||input===null||String(input).trim()==='') return false;
  var n1=parseNum(input), n2=parseNum(answer);
  if(n1!==null && n2!==null){ if(Math.abs(n1-n2)<1e-3) return true; return (accept||[]).some(function(a){ var n3=parseNum(a); return n3!==null && Math.abs(n1-n3)<1e-3; }); }
  var cands=[answer].concat(accept||[]); var ni=norm(input);
  for(var i=0;i<cands.length;i++){ if(norm(cands[i])===ni) return true; }
  return false;
}
function esc(s){ return String(s).replace(/&/g,'&amp;').replace(/</g,'&lt;'); }

/* ================= DATA ================= */
var AR_OPTIONS = ["Both A and R are true, and R is the correct explanation of A","Both A and R are true, but R is NOT the correct explanation of A","A is true but R is false","A is false but R is true"];
var THEORY = "<div class=\"hub\"><div class=\"hub-card\"><h3>📖 Theory notes</h3><p>Explained notes for every part of the chapter, following the book, with the rules and the book’s solved examples.</p><div class=\"hub-btns\"><button class=\"hub-btn\" data-jump=\"n121\">12.1 notes</button><button class=\"hub-btn\" data-jump=\"n122\">12.2 notes</button><button class=\"hub-btn\" data-jump=\"n123\">12.3 notes</button><button class=\"hub-btn\" data-jump=\"n124\">12.4 notes</button><button class=\"hub-btn\" data-jump=\"n125\">12.5 notes</button><button class=\"hub-btn\" data-jump=\"n126\">12.6 notes</button><button class=\"hub-btn\" data-jump=\"n127\">12.7 notes</button></div></div><div class=\"hub-card\"><h3>🎯 Practice by learning objective</h3><p>Every Looking Back, Example, Try This, Exercise and Mental Maths question of the chapter, one sheet per objective, mixing multiple-choice and fill-in-the-blank questions. The bold tag shows where each question is in the book.</p><div class=\"hub-btns\"><button class=\"hub-btn\" data-go=\"s1\">12.1 · Ratio and proportion</button><button class=\"hub-btn\" data-go=\"s2\">12.2 · Direct variation</button><button class=\"hub-btn\" data-go=\"s3\">12.3 · Applications of direct proportion</button><button class=\"hub-btn\" data-go=\"s4\">12.4 · Inverse variation</button><button class=\"hub-btn\" data-go=\"s5\">12.5 · Applications of inverse variation</button><button class=\"hub-btn\" data-go=\"s6\">12.6 · Time and work</button><button class=\"hub-btn\" data-go=\"s7\">12.7 · Time and distance</button></div></div><div class=\"hub-card\"><h3>📝 Learning assessment</h3><p>Four short assessments built from the Chapter Check-up, one per skill area. Take them in Quiz mode and open the report to see your results as pie charts.</p><div class=\"hub-btns\"><button class=\"hub-btn\" data-go=\"s8\">A · Knowing and understanding</button><button class=\"hub-btn\" data-go=\"s9\">B · Investigating patterns</button><button class=\"hub-btn\" data-go=\"s10\">C · Communicating</button><button class=\"hub-btn\" data-go=\"s11\">D · Applying mathematics in real-life contexts</button><button class=\"hub-btn primary\" data-go=\"report\">📊 View my report</button></div></div></div><section class=\"note\" id=\"nintro\"><h2>About this chapter</h2><p>Many quantities change together. Buy more books and you pay more (<b>direct variation</b>); invite more friends to share 60 sweets and each gets fewer (<b>inverse variation</b>). This chapter starts with ratio and proportion and then uses them to solve problems on cost, work, time and distance.</p><p>The practice sheets contain <b>all</b> the questions of the chapter in book order. Each question starts with a tag such as <b>Example 7</b>, <b>Try This</b>, <b>Ex 12A · Q3</b> or <b>Check-up · Q5</b>.</p><div class=\"tscroll\"><table class=\"ttab\"><tr><th>Assessment</th><th>Skill area</th><th>What it checks</th></tr><tr><td>A</td><td>Knowing and understanding</td><td>Ratios, proportions and the rules of variation.</td></tr><tr><td>B</td><td>Investigating patterns</td><td>Spotting constant ratios and constant products in tables.</td></tr><tr><td>C</td><td>Communicating</td><td>Explaining methods, choosing direct or inverse, spotting errors.</td></tr><tr><td>D</td><td>Applying mathematics in real-life contexts</td><td>Cost, recipes, work, trains and journeys, and the Computational Thinking worksheet (a bar graph and a spreadsheet formula).</td></tr></table></div><p><b>Tools:</b> ⏱ at the top times each tab (pause or reset it). ✏️ opens a scratchpad with four pens for rough work. Tap the BM badge to go back to the home page.</p><p><b>Typing answers:</b> a ratio such as 4 : 3 is typed in two boxes (4 and 3). Money is typed without ₹ and without commas (e.g. 11520). Decimals such as 37.5 and fractions such as <span class=\"mono\">56/15</span> or mixed numbers <span class=\"mono\">3 11/15</span> are accepted where the question allows them.</p></section><section class=\"note\" id=\"n121\"><h2>12.1 Ratio and proportion</h2><p class=\"lt\"><b>Objective:</b> Write ratios in simplest form, use proportions (product of extremes = product of means) and share quantities in a given ratio.</p><p>A garden has 30 rose plants and 45 sunflower plants. Comparing <b>by division</b>, the ratio of rose plants to sunflower plants is 30 : 45 (or {30/45}). A <b>ratio</b> compares two quantities of the same kind by division.</p><p>A ratio is in <b>simplest form</b> when its terms are co-prime: divide both terms by their HCF. 30 : 45 = 6 : 9 = <b>2 : 3</b> (HCF 15). The quantities must be in the <b>same unit</b> first; once they are, the units are dropped.</p><div class=\"ex\"><div class=\"exh\">Book Example 2 · 4 m of red ribbon to 7 m 50 cm of green ribbon</div><div class=\"exl\">Same unit: 400 cm : 750 cm.<br>Divide by the HCF 50: <b>8 : 15</b>.</div></div><h4>Proportion</h4><p>A <b>proportion</b> says that two ratios are equivalent: 30 : 45 :: 2 : 3 (read “30 is to 45 as 2 is to 3”). In a : b :: c : d, a and d are the <b>extremes</b> and b and c are the <b>means</b>.</p><p><b>Property of proportionality:</b> product of extremes = product of means, i.e. <b>ad = bc</b> (the cross products of {a/b} = {c/d} are equal).</p><div class=\"ex\"><div class=\"exh\">Book Example 3 · Ratio 4 : 5, first number 60</div><div class=\"exl\">{4/5} = {60/x}.<br>Cross products: 4x = 5 × 60 = 300, so x = <b>75</b>.</div></div><div class=\"ex\"><div class=\"exh\">Book Example 4 · Ratio 8 : 3, sum 132</div><div class=\"exl\">Let the numbers be 8x and 3x: 11x = 132, so x = 12.<br>The numbers are 8 × 12 = <b>96</b> and 3 × 12 = <b>36</b>.</div></div><div class=\"keybox\"><b>Sharing in a ratio:</b> to share ₹1500 in the ratio 2 : 3, add the parts (2 + 3 = 5), find one part (1500 ÷ 5 = 300) and multiply: ₹600 and ₹900.</div><div class=\"hub-btns\" style=\"margin-top:12px\"><button class=\"hub-btn primary\" data-go=\"s1\">Practise 12.1 →</button></div></section><section class=\"note\" id=\"n122\"><h2>12.2 Direct variation</h2><p class=\"lt\"><b>Objective:</b> Recognise direct variation (y ÷ x constant) and find missing values using x₁ : y₁ = x₂ : y₂.</p><p>Shaju treats each friend to a snack costing ₹25. With x friends the cost is y = 25x:</p><div class=\"tscroll\"><table class=\"ttab\"><tr><th>Friends (x)</th><td>1</td><td>2</td><td>3</td><td>4</td><td>5</td><td>6</td><td>10</td></tr><tr><th>Cost y (₹)</th><td>25</td><td>50</td><td>75</td><td>100</td><td>125</td><td>150</td><td>250</td></tr></table></div><p>When x increases, y increases, and {y/x} = 25 every time. Two variables <b>vary directly</b> (are in <b>direct proportion</b>) when {y/x} = k, a constant, i.e. y = kx. Then for two pairs of values x₁/y₁ = x₂/y₂, i.e. <b>x₁ : y₁ :: x₂ : y₂</b>.</p><div class=\"ex\"><div class=\"exh\">Book Example 6 · x varies directly as y; x = 7 when y = 28. Find x when y = 84.</div><div class=\"exl\">{7/28} = {x/84}.<br>28x = 7 × 84, so x = <b>21</b>.</div></div><div class=\"ex\"><div class=\"exh\">Book Example 8 · x varies directly as y<sup>2</sup>; x = 4 when y = 5. Find x when y = 15.</div><div class=\"exl\">x ÷ y<sup>2</sup> is constant: {4/25} = x ÷ 225.<br>x = 4 × 225 ÷ 25 = <b>36</b>.</div></div><div class=\"keybox\"><b>Test for direct variation:</b> divide each y by its x. If every quotient is the same, the variation is direct.</div><div class=\"hub-btns\" style=\"margin-top:12px\"><button class=\"hub-btn primary\" data-go=\"s2\">Practise 12.2 →</button></div></section><section class=\"note\" id=\"n123\"><h2>12.3 Applications of direct proportion</h2><p class=\"lt\"><b>Objective:</b> Solve real-life problems on cost, quantity, speed and distance using direct proportion or the unitary method.</p><p>The money spent is directly proportional to the number of articles bought; the distance travelled at a fixed speed is directly proportional to the time. Write the proportion with the unknown as x and cross-multiply, or use the <b>unitary method</b> (find the value of one first).</p><div class=\"ex\"><div class=\"exh\">Book Example 10 · 8 books cost ₹56. What do 12 books cost?</div><div class=\"exl\">{8/12} = {56/x}.<br>8x = 12 × 56, so x = ₹<b>84</b>.<br>Unitary method: 1 book = ₹7, 12 books = ₹84.</div></div><div class=\"ex\"><div class=\"exh\">Book Example 11 · 24 packets cost ₹96. How many packets for ₹72?</div><div class=\"exl\">{24/x} = {96/72}.<br>96x = 24 × 72, so x = <b>18</b> packets.</div></div><div class=\"keybox\"><b>Check the answer makes sense:</b> in a direct proportion, fewer rupees must buy fewer packets.</div><div class=\"hub-btns\" style=\"margin-top:12px\"><button class=\"hub-btn primary\" data-go=\"s3\">Practise 12.3 →</button></div></section><section class=\"note\" id=\"n124\"><h2>12.4 Inverse variation</h2><p class=\"lt\"><b>Objective:</b> Recognise inverse variation (x × y constant), tell direct from inverse variation and find missing values.</p><p>Share 60 sweets among x friends; each gets y sweets:</p><div class=\"tscroll\"><table class=\"ttab\"><tr><th>Friends (x)</th><td>1</td><td>2</td><td>3</td><td>4</td><td>5</td><td>6</td><td>10</td><td>20</td><td>60</td></tr><tr><th>Sweets each (y)</th><td>60</td><td>30</td><td>20</td><td>15</td><td>12</td><td>10</td><td>6</td><td>3</td><td>1</td></tr></table></div><p>As x increases, y decreases, and <b>x × y = 60</b> every time. Such variables <b>vary inversely</b> (are in <b>inverse proportion</b>): xy = k, a constant. Then x₁y₁ = x₂y₂, which can be written x₁/x₂ = y₂/y₁, i.e. <b>x₁ : x₂ :: y₂ : y₁</b>.</p><div class=\"ex\"><div class=\"exh\">Book Example 12 · x varies inversely as y; x = 6 when y = 6. Find x when y = 9.</div><div class=\"exl\">x₁ : x₂ :: y₂ : y₁ gives 6 : x :: 9 : 6.<br>9x = 36, so x = <b>4</b>.</div></div><div class=\"ex\"><div class=\"exh\">Book Example 13(b) · Direct or inverse?</div><div class=\"exl\">x: 1, 2, 4, 5, 10 and y: 100, 50, 25, 20, 10.<br>Every product xy = 100, so it is an <b>inverse</b> variation; e.g. 2 : 5 :: 20 : 50.</div></div><div class=\"keybox\"><b>Direct:</b> the quotient y ÷ x is constant. <b>Inverse:</b> the product x × y is constant. “One goes up, the other goes down” alone is not enough; the product must stay the same.</div><div class=\"hub-btns\" style=\"margin-top:12px\"><button class=\"hub-btn primary\" data-go=\"s4\">Practise 12.4 →</button></div></section><section class=\"note\" id=\"n125\"><h2>12.5 Applications of inverse variation</h2><p class=\"lt\"><b>Objective:</b> Solve problems on workers, food supplies, speed and time using inverse proportion, including problems with three variables.</p><p>More workers finish a job in fewer days; more soldiers finish the food sooner; a faster car takes less time for the same journey. In each case use x₁ : x₂ :: y₂ : y₁ (or x₁y₁ = x₂y₂).</p><div class=\"ex\"><div class=\"exh\">Book Example 14 · Money for 30 books at ₹20 each. How many at ₹25?</div><div class=\"exl\">20 : 25 :: y : 30.<br>25y = 20 × 30, so y = <b>24</b> books.</div></div><div class=\"ex\"><div class=\"exh\">Book Example 15 · Food for 800 soldiers for 60 days; 400 more arrive.</div><div class=\"exl\">Now 1200 soldiers: 800 : 1200 :: x : 60.<br>1200x = 60 × 800, so x = <b>40</b> days.</div></div><h4>Three variables</h4><p>When three quantities change, take two at a time and keep the third fixed. <b>Example 17:</b> ₹3200 feeds 20 students for 30 days. With 30 students (money fixed) the rice lasts 20 × 30 ÷ 30 = 20 days (inverse). With ₹2400 instead of ₹3200 (students fixed) it lasts 20 × 2400 ÷ 3200 = <b>15 days</b> (direct).</p><div class=\"keybox\"><b>Person-hours:</b> in work problems, men × hours per day × days measures the total work. 10 men × 7 hours × 12 days = 840 person-hours.</div><div class=\"hub-btns\" style=\"margin-top:12px\"><button class=\"hub-btn primary\" data-go=\"s5\">Practise 12.5 →</button></div></section><section class=\"note\" id=\"n126\"><h2>12.6 Time and work</h2><p class=\"lt\"><b>Objective:</b> Use the work done in one day (or one minute) to solve problems on people working together, pipes and leaks.</p><p>If a person finishes a piece of work in n days, in <b>one day</b> the person does {1/n} of the work. If a tap fills a tank in m minutes, it fills {1/m} of the tank in one minute. Add the parts for people (or inlets) working together; subtract for a leak or an outlet.</p><div class=\"ex\"><div class=\"exh\">Book Example 18 · Satish: 6 days, Ritesh: 12 days</div><div class=\"exl\">One day together: {1/6} + {1/12} = {3/12} = {1/4} of the house.<br>Whole house: 1 ÷ {1/4} = <b>4 days</b>.</div></div><div class=\"ex\"><div class=\"exh\">Book Example 19 · Inlets filling a tank in 30, 40 and 60 minutes</div><div class=\"exl\">One minute: {1/30} + {1/40} + {1/60} = {9/120} of the tank.<br>Time = {120/9} = {40/3} = {13 1/3} minutes = <b>13 min 20 s</b>.</div></div><div class=\"keybox\"><b>Leaks and outlets:</b> a tap filling in 2 h with a leak making it 5 h: the leak empties {1/2} − {1/5} = {3/10} of the tank per hour, so alone it empties a full tank in {10/3} h.</div><div class=\"hub-btns\" style=\"margin-top:12px\"><button class=\"hub-btn primary\" data-go=\"s6\">Practise 12.6 →</button></div></section><section class=\"note\" id=\"n127\"><h2>12.7 Time and distance</h2><p class=\"lt\"><b>Objective:</b> Use speed = distance ÷ time, convert between km/h and m/s, and solve problems on trains crossing posts, bridges and platforms.</p><p><b>Speed = distance ÷ time</b>, so distance = speed × time and time = distance ÷ speed. At a fixed speed, distance and time vary directly; for a fixed distance, speed and time vary inversely.</p><p><b>Units:</b> 1 km/h = {1000/3600} m/s = {5/18} m/s, and 1 m/s = {18/5} km/h. So 45 km/h = 45 × {5/18} = 12.5 m/s.</p><h4>Trains</h4><ul><li>To pass a signal post, a pole or a standing person, a train covers <b>its own length</b>.</li><li>To cross a bridge or a platform, it covers <b>its own length + the length of the bridge or platform</b>.</li></ul><svg class=\"figsvg\" viewBox=\"0 0 330 96\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><rect x=\"20\" y=\"28\" width=\"90\" height=\"22\" rx=\"4\" style=\"fill:var(--gold-soft);stroke:var(--ink);stroke-width:1.2\"/><text class=\"lb\" x=\"65.0\" y=\"39.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">train 350 m</text><line class=\"ln\" x1=\"110.0\" y1=\"54.0\" x2=\"310.0\" y2=\"54.0\"/><text class=\"lb\" x=\"210.0\" y=\"44.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">bridge 750 m</text><line class=\"ln\" x1=\"20.0\" y1=\"78.0\" x2=\"310.0\" y2=\"78.0\" marker-end=\"url(#ah)\" marker-start=\"url(#ahs)\"/><text class=\"al\" x=\"165.0\" y=\"89.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">distance covered = 350 + 750 = 1100 m</text></svg><div class=\"ex\"><div class=\"exh\">Book Example 20 · A 375 m train at 45 km/h passes a signal post</div><div class=\"exl\">45 km/h = 45000 m in 3600 s.<br>Time = 375 × 3600 ÷ 45000 = <b>30 s</b>.</div></div><div class=\"ex\"><div class=\"exh\">Book Example 21 · A 350 m train crosses a 750 m bridge at 55 km/h</div><div class=\"exl\">Distance = 350 + 750 = 1100 m.<br>Time = 1100 × 3600 ÷ 55000 = <b>72 s</b>.</div></div><div class=\"keybox\"><b>Common mistake:</b> the distance covered while crossing a platform is NOT just the platform length; add the length of the train.</div><div class=\"hub-btns\" style=\"margin-top:12px\"><button class=\"hub-btn primary\" data-go=\"s7\">Practise 12.7 →</button></div></section><section class=\"note\" id=\"nsum\"><h2>Chapter checklist</h2><ul><li>Write ratios in simplest form, use proportions (product of extremes = product of means) and share quantities in a given ratio.</li><li>Recognise direct variation (y ÷ x constant) and find missing values using x₁ : y₁ = x₂ : y₂.</li><li>Solve real-life problems on cost, quantity, speed and distance using direct proportion or the unitary method.</li><li>Recognise inverse variation (x × y constant), tell direct from inverse variation and find missing values.</li><li>Solve problems on workers, food supplies, speed and time using inverse proportion, including problems with three variables.</li><li>Use the work done in one day (or one minute) to solve problems on people working together, pipes and leaks.</li><li>Use speed = distance ÷ time, convert between km/h and m/s, and solve problems on trains crossing posts, bridges and platforms.</li></ul><div class=\"hub-btns\" style=\"margin-top:10px\"><button class=\"hub-btn\" data-go=\"s8\">Assessment A</button><button class=\"hub-btn\" data-go=\"s9\">Assessment B</button><button class=\"hub-btn\" data-go=\"s10\">Assessment C</button><button class=\"hub-btn\" data-go=\"s11\">Assessment D</button><button class=\"hub-btn primary\" data-go=\"report\">📊 Report</button></div></section>";
var REPORT = [["s8", "A", "Knowing and understanding"], ["s9", "B", "Investigating patterns"], ["s10", "C", "Communicating"], ["s11", "D", "Applying mathematics in real-life contexts"]];
var SECTIONS = [{"id": "s1", "label": "12.1 Ratio & proportion", "sub": "Ratios in simplest form, proportions and sharing in a ratio", "slides": [{"kind": "blank", "p": "<b>Looking Back · Q1</b> · Express the ratio of ₹8 and ₹5.50 in simplest form.", "tag": "", "marks": "", "flat": [{"t": "In paise: 800 : __B1__", "a": {"B1": "550"}}, {"t": "Simplest form = __B1__ : __B2__", "a": {"B1": "16", "B2": "11"}}], "sol": "₹8 = 800 paise and ₹5.50 = 550 paise.\nHCF(800, 550) = 50: 800 : 550 = 16 : 11."}, {"kind": "mcq", "text": "<b>Looking Back · Q2</b> · Compare the ratios 8 : 11 and 11 : 15.", "opts": ["8 : 11 > 11 : 15", "8 : 11 < 11 : 15", "8 : 11 = 11 : 15", "They cannot be compared"], "correct": 1, "tag": "", "sol": "{8/11} = {120/165} and {11/15} = {121/165} (LCM 165). 120 < 121, so 8 : 11 < 11 : 15."}, {"kind": "blank", "p": "<b>Looking Back · Q3</b> · Two numbers are in the ratio 10 : 17 and their difference is 42. What are the two numbers?", "tag": "", "marks": "", "flat": [{"t": "Let them be 10x and 17x: 7x = 42, so x = __B1__", "a": {"B1": "6"}}, {"t": "The numbers are __B1__ and __B2__", "a": {"B1": "60", "B2": "102"}}], "sol": "17x − 10x = 7x = 42, so x = 6.\n10 × 6 = 60 and 17 × 6 = 102."}, {"kind": "mcq", "text": "<b>Example 1</b> · Class VIII has 48 boys and 36 girls. Write the ratio of the boys to girls in the simplest form.", "opts": ["8 : 6", "3 : 4", "4 : 3", "12 : 9"], "correct": 2, "tag": "", "sol": "48 : 36; divide both by the HCF 12: 48 ÷ 12 : 36 ÷ 12 = 4 : 3. (12 : 9 and 8 : 6 are equal ratios but not the simplest.)"}, {"kind": "blank", "p": "<b>Example 2</b> · Arun has 4 m of red ribbon and 7 m 50 cm of green ribbon. Find the simplest ratio of the lengths of red ribbon to green ribbon.", "tag": "", "marks": "", "flat": [{"t": "In cm: __B1__ : __B2__", "a": {"B1": "400", "B2": "750"}}, {"t": "Simplest ratio = __B1__ : __B2__", "a": {"B1": "8", "B2": "15"}}], "sol": "4 m = 400 cm and 7 m 50 cm = 750 cm (same unit first).\nDivide by the HCF 50: 8 : 15."}, {"kind": "mcq", "text": "<b>Example 3</b> · Two numbers are in the ratio of 4 : 5. The first number is 60. What is the other number?", "opts": ["48", "80", "75", "65"], "correct": 2, "tag": "", "sol": "{4/5} = {60/x}. Cross products: 4x = 5 × 60 = 300, so x = 75."}, {"kind": "blank", "p": "<b>Example 4</b> · Two numbers are in the ratio 8 : 3 and their sum is 132. Find the numbers.", "tag": "", "marks": "", "flat": [{"t": "8x + 3x = 11x = 132, so x = __B1__", "a": {"B1": "12"}}, {"t": "The numbers are __B1__ and __B2__", "a": {"B1": "96", "B2": "36"}}], "sol": "11x = 132, x = 12.\n8 × 12 = 96 and 3 × 12 = 36."}, {"kind": "blank", "p": "<b>Example 5</b> · Two numbers are in the ratio 4 : 1. If 5 is added to both the numbers, the smaller number exactly divides the larger number, giving the quotient 3. Find the numbers.", "tag": "", "marks": "", "flat": [{"t": "(4x + 5) ÷ (x + 5) = 3 gives 4x + 5 = 3x + 15, so x = __B1__", "a": {"B1": "10"}}, {"t": "Larger number = __B1__, smaller number = __B2__", "a": {"B1": "40", "B2": "10"}}], "sol": "Cross-multiply: 4x + 5 = 3(x + 5) = 3x + 15; transposing, 4x − 3x = 15 − 5, x = 10.\nLarger = 4x = 40, smaller = x = 10. Check: 45 ÷ 15 = 3."}, {"kind": "mcq", "text": "<b>Try This · Q1</b> · Express as ratios in the simplest form:  a) 5 ℓ to 12 ℓ   b) 3 pens to 9 pens", "opts": ["a) 12 : 5  b) 3 : 1", "a) 5 : 12  b) 3 : 9", "a) 1 : 2  b) 1 : 3", "a) 5 : 12  b) 1 : 3"], "correct": 3, "tag": "", "sol": "a) HCF(5, 12) = 1, so 5 : 12 is already simplest. b) Divide by 3: 3 : 9 = 1 : 3."}, {"kind": "blank", "p": "<b>Try This · Q2</b> · Two numbers are in the ratio 3 : 5 and their difference is 22. Find the numbers.", "tag": "", "marks": "", "flat": [{"t": "5x − 3x = 2x = 22, so x = __B1__", "a": {"B1": "11"}}, {"t": "The numbers are __B1__ and __B2__", "a": {"B1": "33", "B2": "55"}}], "sol": "2x = 22, x = 11.\n3 × 11 = 33 and 5 × 11 = 55."}, {"kind": "mcq", "text": "<b>Try This · Q3</b> · Find the value of x in the proportion {4/7} = {x/21}.", "opts": ["7", "12", "28", "3"], "correct": 1, "tag": "", "sol": "Cross products: 7x = 4 × 21 = 84, so x = 12. (21 = 7 × 3, so x = 4 × 3.)"}, {"kind": "blank", "p": "<b>Ex 12A · Q1(a–c)</b> · Represent the ratio of the first number to the second in the simplest form.", "tag": "", "marks": "", "flat": [{"t": "a) 6, 9 → __B1__ : __B2__", "a": {"B1": "2", "B2": "3"}}, {"t": "b) 18, 16 → __B1__ : __B2__", "a": {"B1": "9", "B2": "8"}}, {"t": "c) 16, 48 → __B1__ : __B2__", "a": {"B1": "1", "B2": "3"}}], "sol": "HCF 3: 2 : 3.\nHCF 2: 9 : 8.\nHCF 16: 1 : 3."}, {"kind": "blank", "p": "<b>Ex 12A · Q1(d–f)</b> · Represent the ratio of the first number to the second in the simplest form.", "tag": "", "marks": "", "flat": [{"t": "d) 88, 28 → __B1__ : __B2__", "a": {"B1": "22", "B2": "7"}}, {"t": "e) 10, 49 → __B1__ : __B2__", "a": {"B1": "10", "B2": "49"}}, {"t": "f) 108, 64 → __B1__ : __B2__", "a": {"B1": "27", "B2": "16"}}], "sol": "HCF 4: 22 : 7.\nHCF 1: 10 : 49 is already in simplest form.\nHCF 4: 27 : 16."}, {"kind": "mcq", "text": "<b>Ex 12A · Q2(a–d)</b> · Express as ratios:  a) 5 m to 7 m   b) ₹3 to ₹8   c) 4 h to 80 min   d) 1 m to 20 cm", "opts": ["a) 5 : 7  b) 3 : 8  c) 1 : 20  d) 1 : 20", "a) 5 : 7  b) 3 : 8  c) 3 : 1  d) 5 : 1", "a) 7 : 5  b) 8 : 3  c) 1 : 3  d) 1 : 5", "a) 5 : 7  b) 3 : 8  c) 4 : 80  d) 5 : 1"], "correct": 1, "tag": "", "sol": "a) 5 : 7. b) 3 : 8. c) 4 h = 240 min; 240 : 80 = 3 : 1. d) 1 m = 100 cm; 100 : 20 = 5 : 1. Always change to the same unit first."}, {"kind": "blank", "p": "<b>Ex 12A · Q2(e–g)</b> · Express the following quantities as ratios in simplest form.", "tag": "", "marks": "", "flat": [{"t": "e) 18 m to 20 m → __B1__ : __B2__", "a": {"B1": "9", "B2": "10"}}, {"t": "f) 27 kg to 36 kg → __B1__ : __B2__", "a": {"B1": "3", "B2": "4"}}, {"t": "g) 5 shirts to 20 shirts → __B1__ : __B2__", "a": {"B1": "1", "B2": "4"}}], "sol": "HCF 2: 9 : 10.\nHCF 9: 3 : 4.\nHCF 5: 1 : 4."}, {"kind": "blank", "p": "<b>Ex 12A · Q3</b> · Express the ratios in the standard form or simplest form.", "tag": "", "marks": "", "flat": [{"t": "a) {12/20} = __B1__", "a": {"B1": "3/5"}, "expr": "fl"}, {"t": "b) {8/16} = __B1__", "a": {"B1": "1/2"}, "expr": "fl"}, {"t": "c) {24/36} = __B1__", "a": {"B1": "2/3"}, "expr": "fl"}, {"t": "d) {15/25} = __B1__", "a": {"B1": "3/5"}, "expr": "fl"}, {"t": "e) {6/8} = __B1__", "a": {"B1": "3/4"}, "expr": "fl"}, {"t": "f) {14/42} = __B1__", "a": {"B1": "1/3"}, "expr": "fl"}], "sol": "HCF 4: {3/5}.\nHCF 8: {1/2}.\nHCF 12: {2/3}.\nHCF 5: {3/5}.\nHCF 2: {3/4}.\nHCF 14: {1/3}."}, {"kind": "mcq", "text": "<b>Ex 12A · Q4(a–c)</b> · Find the value of x in the given proportions:  a) {3/8} = {6/x}   b) {4/5} = {12/x}   c) x : 4 :: 5 : 2", "opts": ["a) 4  b) 15  c) 10", "a) 16  b) 9  c) 2.5", "a) 16  b) 15  c) 8", "a) 16  b) 15  c) 10"], "correct": 3, "tag": "", "sol": "a) 3x = 48, x = 16. b) 4x = 60, x = 15. c) Product of extremes = product of means: 2x = 4 × 5 = 20, x = 10."}, {"kind": "blank", "p": "<b>Ex 12A · Q4(d–f)</b> · Find the value of x in the given proportions.", "tag": "", "marks": "", "flat": [{"t": "d) 5 : 4 :: x : 30 → x = __B1__", "a": {"B1": "75/2"}, "expr": "fv"}, {"t": "e) {8/9} = {x/81} → x = __B1__", "a": {"B1": "72"}}, {"t": "f) {6/9} = 2 ÷ (x + 1) → x = __B1__", "a": {"B1": "2"}}], "sol": "Product of means = product of extremes: 4x = 5 × 30 = 150, x = 37.5.\n9x = 8 × 81, x = 72.\n6(x + 1) = 18, so x + 1 = 3 and x = 2."}, {"kind": "blank", "p": "<b>Ex 12A · Q5</b> · Nimmi’s collection of Indian stamps to foreign stamps is in the ratio 4 : 7. If she has 68 Indian stamps, how many foreign stamps does she have?", "tag": "", "marks": "", "flat": [{"t": "Foreign stamps = __B1__", "a": {"B1": "119"}}], "sol": "{4/7} = {68/x}: 4x = 476, x = 119."}, {"kind": "mcq", "text": "<b>Ex 12A · Q6</b> · The pocket money which Ravi and Suman have in their hands are in the ratio 8 : 9. If Suman has ₹198 with her, how much does Ravi have?", "opts": ["₹189", "₹222", "₹176", "₹160"], "correct": 2, "tag": "", "sol": "{8/9} = {x/198}: 9x = 8 × 198 = 1584, x = ₹176."}, {"kind": "blank", "p": "<b>Ex 12A · Q7</b> · The monthly incomes of Sonu and Raja are ₹14,400 and ₹12,800. Find the ratio of Sonu’s salary to Raja’s salary in the simplest form.", "tag": "", "marks": "", "flat": [{"t": "Sonu : Raja = __B1__ : __B2__", "a": {"B1": "9", "B2": "8"}}], "sol": "14400 : 12800; divide by the HCF 1600: 9 : 8."}, {"kind": "mcq", "text": "<b>Mental Maths · Q1</b> · The incomes of Jagat and Mohit per month are ₹30,000 and ₹36,000 respectively. What is the simplest ratio of the salaries of Mohit and Jagat?", "opts": ["36 : 30", "6 : 5", "5 : 6", "1 : 6"], "correct": 1, "tag": "", "sol": "Mohit : Jagat = 36000 : 30000; divide by 6000: 6 : 5. (Note the order: Mohit first.)"}, {"kind": "blank", "p": "<b>Mental Maths · Q2</b> · A sum of ₹1500 is shared between Sangeeta and Leela in the ratio 2 : 3. How much are their shares?", "tag": "", "marks": "", "flat": [{"t": "Sangeeta gets ₹__B1__ and Leela gets ₹__B2__", "a": {"B1": "600", "B2": "900"}}], "sol": "2 + 3 = 5 parts; one part = 1500 ÷ 5 = ₹300. Sangeeta 2 × 300 = ₹600, Leela 3 × 300 = ₹900."}, {"kind": "mcq", "text": "<b>Mental Maths · Q3</b> · A collection of marbles was divided between Raju and Biju in the ratio 4 : 5. If Biju’s share was 125 marbles, how many marbles did Raju get?", "opts": ["125", "100", "225", "156"], "correct": 1, "tag": "", "sol": "One part = 125 ÷ 5 = 25, so Raju gets 4 × 25 = 100 marbles."}, {"kind": "blank", "p": "<b>Mental Maths · Q4</b> · The length of a cloth is 60 metres. It is cut in the ratio 2 : 3 : 5. What are the lengths of each of the parts?", "tag": "", "marks": "", "flat": [{"t": "The parts are __B1__ m, __B2__ m and __B3__ m", "a": {"B1": "12", "B2": "18", "B3": "30"}}], "sol": "2 + 3 + 5 = 10 parts; one part = 6 m. Lengths 12 m, 18 m and 30 m."}]}, {"id": "s2", "label": "12.2 Direct variation", "sub": "x ÷ y constant; finding missing values in a direct variation", "slides": [{"kind": "blank", "p": "<b>Example 6</b> · If x varies directly as y and x = 7 when y = 28, find x when y is 84.", "tag": "", "marks": "", "flat": [{"t": "{7/28} = {x/84}: 28x = 7 × 84, so x = __B1__", "a": {"B1": "21"}}, {"t": "The proportion is 7 : 28 :: __B1__ : 84", "a": {"B1": "21"}}], "sol": "28x = 588, x = 21.\n7 : 28 :: 21 : 84."}, {"kind": "mcq", "text": "<b>Example 7</b> · If x varies directly as 3y and x = 3 when y = 4, find x when y = 12.", "opts": ["3", "9", "36", "1"], "correct": 1, "tag": "", "sol": "x ÷ 3y is constant: {3/12} = {x/36} (3y = 3 × 12 = 36). 12x = 108, so x = 9. Check with the proportion 3 : 12 :: 9 : 36."}, {"kind": "blank", "p": "<b>Example 8</b> · If x varies directly as y<sup>2</sup> and x = 4 when y = 5, then find x when y is 15.", "tag": "", "marks": "", "flat": [{"t": "When y = 5, y<sup>2</sup> = 25; when y = 15, y<sup>2</sup> = __B1__", "a": {"B1": "225"}}, {"t": "{4/25} = x ÷ 225, so x = __B1__", "a": {"B1": "36"}}], "sol": "15<sup>2</sup> = 225.\nx = 4 × 225 ÷ 25 = 36, so x : y<sup>2</sup> = 4 : 25 :: 36 : 225."}, {"kind": "mcq", "text": "<b>Example 9</b> · If v varies directly as t and v = 19.6 when t = 2, find v when t = 3.", "opts": ["13.07", "9.8", "29.4", "39.2"], "correct": 2, "tag": "", "sol": "19.6/2 = v ÷ 3, so v = 9.8 × 3 = 29.4."}, {"kind": "blank", "p": "<b>Try This</b> · If x and y vary directly, find the missing quantities in the table.", "tag": "", "marks": "", "flat": [{"t": "x when y = 12: __B1__", "a": {"B1": "3"}}, {"t": "y when x = 1: __B1__", "a": {"B1": "4"}}, {"t": "x when y = 16: __B1__", "a": {"B1": "4"}}], "sol": "y ÷ x = 8 ÷ 2 = 4, so y = 4x. 12 ÷ 4 = 3.\ny = 4 × 1 = 4.\n16 ÷ 4 = 4.", "fig": "<svg class=\"figsvg\" viewBox=\"0 0 150 62\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><rect x=\"4.0\" y=\"4\" width=\"28.0\" height=\"26\" style=\"fill:var(--paper-2);stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"18.0\" y=\"18.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">x</text><rect x=\"32.0\" y=\"4\" width=\"28.0\" height=\"26\" style=\"fill:none;stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"46.0\" y=\"18.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">2</text><rect x=\"60.0\" y=\"4\" width=\"29.0\" height=\"26\" style=\"fill:none;stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"74.5\" y=\"18.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">?</text><rect x=\"89.0\" y=\"4\" width=\"28.0\" height=\"26\" style=\"fill:none;stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"103.0\" y=\"18.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">1</text><rect x=\"117.0\" y=\"4\" width=\"29.0\" height=\"26\" style=\"fill:none;stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"131.5\" y=\"18.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">?</text><rect x=\"4.0\" y=\"30\" width=\"28.0\" height=\"26\" style=\"fill:var(--paper-2);stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"18.0\" y=\"44.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">y</text><rect x=\"32.0\" y=\"30\" width=\"28.0\" height=\"26\" style=\"fill:none;stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"46.0\" y=\"44.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">8</text><rect x=\"60.0\" y=\"30\" width=\"29.0\" height=\"26\" style=\"fill:none;stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"74.5\" y=\"44.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">12</text><rect x=\"89.0\" y=\"30\" width=\"28.0\" height=\"26\" style=\"fill:none;stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"103.0\" y=\"44.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">?</text><rect x=\"117.0\" y=\"30\" width=\"29.0\" height=\"26\" style=\"fill:none;stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"131.5\" y=\"44.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">16</text></svg>"}, {"kind": "mcq", "text": "<b>Ex 12B · Q1</b> · Do these three representations of the ratio of 5 to 7 give the same value?  a) 5 to 7   b) 5 : 7   c) {5/7}", "opts": ["No, only a and b are the same", "No, all three are different", "No, only b and c are the same", "Yes, all three give the same value"], "correct": 3, "tag": "", "sol": "“5 to 7”, “5 : 7” and {5/7} are three ways of writing the same ratio, the quotient 5 ÷ 7."}, {"kind": "blank", "p": "<b>Ex 12B · Q2</b> · If x varies directly as y and", "tag": "", "marks": "", "flat": [{"t": "a) x = 10 when y = 6, find y when x = 35: y = __B1__", "a": {"B1": "21"}}, {"t": "b) x = 9 when y = 15, find x when y = 45: x = __B1__", "a": {"B1": "27"}}, {"t": "c) x = 14 when y = 16, find y when x = 42: y = __B1__", "a": {"B1": "48"}}, {"t": "d) x = 22 when y = 12, find y when x = 11: y = __B1__", "a": {"B1": "6"}}, {"t": "e) x = 7 when y = 36, find y when x = 21: y = __B1__", "a": {"B1": "108"}}], "sol": "{10/6} = {35/y}: 10y = 210, y = 21.\n{9/15} = {x/45}: 15x = 405, x = 27.\n{14/16} = {42/y}: 14y = 672, y = 48.\n{22/12} = {11/y}: 22y = 132, y = 6.\n{7/36} = {21/y}: 7y = 756, y = 108."}, {"kind": "mcq", "text": "<b>Ex 12B · Q3</b> · When x varies directly as 2y and  a) x = 4 when y = 18, find x when y = 36;  b) x = 6 when y = 20, find y when x = 9.", "opts": ["a) x = 8  b) y = 30", "a) x = 8  b) y = 15", "a) x = 2  b) y = 13.3", "a) x = 16  b) y = 30"], "correct": 0, "tag": "", "sol": "a) x ÷ 2y is constant: {4/36} = {x/72}, so x = 8. b) {6/40} = 9 ÷ 2y, so 2y = 60 and y = 30."}, {"kind": "blank", "p": "<b>Ex 12B · Q4</b> · If x varies directly as 3y and", "tag": "", "marks": "", "flat": [{"t": "a) x = 8 when y = 3, find x when y = 27: x = __B1__", "a": {"B1": "72"}}, {"t": "b) x = 7 when y = 5, find y when x = 14: y = __B1__", "a": {"B1": "10"}}], "sol": "{8/9} = {x/81} (3y = 81): x = 72.\n{7/15} = 14 ÷ 3y: 3y = 30, y = 10."}, {"kind": "mcq", "text": "<b>Ex 12B · Q5(a–h)</b> · Identify the variables which are in direct proportion. Which one of these is NOT a direct proportion?  a) quantity of food and its cost  b) number of people and consumption of food  c) height of a tree and the number of years  d) number of notebooks and their cost  e) time taken and distance travelled (same speed)  f) funds collected and number of people who contributed  g) distance travelled by a train and its speed (same time)  h) number of people working and quantity of work done (each doing the same work)", "opts": ["e) time taken and distance travelled (same speed)", "a) quantity of food and its cost", "c) height of a tree and the number of years", "d) number of notebooks and their cost"], "correct": 2, "tag": "", "sol": "A tree does not grow by the same amount every year, so c) is not a direct proportion. All the others increase together at a constant rate (for f, assuming each person gives the same amount)."}, {"kind": "mcq", "text": "<b>Ex 12B · Q5(i–n)</b> · Which of these is NOT a direct proportion?  i) number of people working and time to complete a given work  j) number of days worked and quantity of work done (same number of people)  k) interest on money and the amount invested  l) interest and the rate of interest  m) commission on sale and amount of sale  n) income tax and the income", "opts": ["k) interest on money and the amount invested", "i) number of people working and time to complete a given work", "m) commission on sale and amount of sale", "j) number of days worked and quantity of work done"], "correct": 1, "tag": "", "sol": "i) More people finish the work in less time: that is an inverse variation. j), k), l), m) and n) (at a fixed rate) increase together in the same ratio: direct proportion."}]}, {"id": "s3", "label": "12.3 Direct proportion problems", "sub": "Cost, quantity, speed and distance using direct proportion", "slides": [{"kind": "blank", "p": "<b>Looking Back · Q4</b> · The cost of 8 copies of a book is ₹488. Find the cost of 13 copies of the same book at the same rate.", "tag": "", "marks": "", "flat": [{"t": "Cost of 1 copy = ₹__B1__", "a": {"B1": "61"}}, {"t": "Cost of 13 copies = ₹__B1__", "a": {"B1": "793"}}], "sol": "488 ÷ 8 = ₹61.\n61 × 13 = ₹793."}, {"kind": "mcq", "text": "<b>Looking Back · Q5</b> · If 15 burgers cost ₹1425, what will be the cost of 5 such burgers?", "opts": ["₹285", "₹4275", "₹475", "₹95"], "correct": 2, "tag": "", "sol": "1 burger = 1425 ÷ 15 = ₹95; 5 burgers = ₹475 (or 1425 ÷ 3, since 5 is a third of 15)."}, {"kind": "blank", "p": "<b>Example 10</b> · Mary purchased 8 books for ₹56. Jane purchased 12 books. How much did Jane pay?", "tag": "", "marks": "", "flat": [{"t": "{8/12} = {56/x}: 8x = 12 × 56 = __B1__", "a": {"B1": "672"}}, {"t": "Jane paid ₹__B1__", "a": {"B1": "84"}}], "sol": "Mary’s books : Jane’s books :: ₹56 : ₹x; cross-multiply: 8x = 672.\nx = 672 ÷ 8 = ₹84."}, {"kind": "mcq", "text": "<b>Example 11</b> · John purchased 24 packets of crayons for ₹96. How many packets of the same crayons can be purchased for ₹72?", "opts": ["18", "20", "12", "32"], "correct": 0, "tag": "", "sol": "{24/x} = {96/72}: 96x = 24 × 72 = 1728, x = 18 packets."}, {"kind": "blank", "p": "<b>Try This · Q1</b> · If 40 ℓ of petrol costs ₹2400, how many litres of petrol can be purchased for ₹420?", "tag": "", "marks": "", "flat": [{"t": "Litres = __B1__", "a": {"B1": "7"}}], "sol": "1 ℓ costs 2400 ÷ 40 = ₹60, so ₹420 buys 420 ÷ 60 = 7 ℓ."}, {"kind": "mcq", "text": "<b>Try This · Q2</b> · If 3 men can earn ₹660 per day, how much would 15 men earn per day?", "opts": ["₹132", "₹3300", "₹1980", "₹220"], "correct": 1, "tag": "", "sol": "1 man earns 660 ÷ 3 = ₹220; 15 men earn 15 × 220 = ₹3300."}, {"kind": "blank", "p": "<b>Ex 12C · Q1</b> · Alice said that the ratio of her weight to that of Joan is 8 : 9. If Alice weighs 40 kg, what is the weight of Joan?", "tag": "", "marks": "", "flat": [{"t": "Joan’s weight = __B1__ kg", "a": {"B1": "45"}}], "sol": "{8/9} = {40/x}: 8x = 360, x = 45 kg."}, {"kind": "mcq", "text": "<b>Ex 12C · Q2</b> · The cost of apples and oranges is in the ratio of 6 : 9 per box. If a box of oranges costs ₹90, what is the cost of a box of apples?", "opts": ["₹60", "₹81", "₹54", "₹135"], "correct": 0, "tag": "", "sol": "{6/9} = {x/90}: 9x = 540, x = ₹60."}, {"kind": "blank", "p": "<b>Ex 12C · Q3</b> · The speeds of two trains are in the ratio 4 : 5. If the speed of the first train is 48 km/h, what is the speed of the other train?", "tag": "", "marks": "", "flat": [{"t": "Speed = __B1__ km/h", "a": {"B1": "60"}}], "sol": "{4/5} = {48/x}: 4x = 240, x = 60 km/h."}, {"kind": "blank", "p": "<b>Ex 12C · Q4</b> · Raman drives 120 km in {2 1/2} hours. How many kilometres does he drive in one hour?", "tag": "", "marks": "", "flat": [{"t": "Distance in 1 hour = __B1__ km", "a": {"B1": "48"}}], "sol": "120 ÷ {5/2} = 120 × {2/5} = 48 km."}, {"kind": "mcq", "text": "<b>Ex 12C · Q5</b> · Daisy uses up 3 litres of petrol for riding 100 km on her scooter. How many litres of petrol does she use for riding 400 km?", "opts": ["7 litres", "1.2 litres", "12 litres", "133 litres"], "correct": 2, "tag": "", "sol": "400 km is 4 times 100 km, so she uses 4 × 3 = 12 litres."}, {"kind": "blank", "p": "<b>Ex 12C · Q6</b> · Jania can jog 3.5 km in one hour. At the same rate, how many kilometres can she jog in 3 hours?", "tag": "", "marks": "", "flat": [{"t": "Distance = __B1__ km", "a": {"B1": "21/2"}, "expr": "fv"}], "sol": "3.5 × 3 = 10.5 km."}, {"kind": "blank", "p": "<b>Ex 12C · Q7</b> · An aeroplane flies 1600 km in 2 hours. At the same rate, how long will it take to fly 6400 km?", "tag": "", "marks": "", "flat": [{"t": "Time = __B1__ hours", "a": {"B1": "8"}}], "sol": "{1600/6400} = {2/x}: 1600x = 12800, x = 8 hours."}, {"kind": "mcq", "text": "<b>Ex 12C · Q8</b> · For every five days of work, Birender gets two days of holidays. If he works for 20 days, how many days of holidays can he enjoy?", "opts": ["4", "10", "50", "8"], "correct": 3, "tag": "", "sol": "{5/2} = {20/x}: 5x = 40, x = 8 days."}, {"kind": "blank", "p": "<b>Ex 12C · Q9</b> · If 10 books cost ₹1170, how many books can be purchased for ₹2925?", "tag": "", "marks": "", "flat": [{"t": "Cost of one book = ₹__B1__", "a": {"B1": "117"}}, {"t": "Number of books = __B1__", "a": {"B1": "25"}}], "sol": "1170 ÷ 10 = ₹117.\n2925 ÷ 117 = 25 books."}, {"kind": "blank", "p": "<b>Ex 12C · Q10</b> · If 7 kg of salt costs ₹112, find the cost of 25 kg of salt.", "tag": "", "marks": "", "flat": [{"t": "Cost = ₹__B1__", "a": {"B1": "400"}}], "sol": "1 kg costs 112 ÷ 7 = ₹16, so 25 kg cost 25 × 16 = ₹400."}, {"kind": "mcq", "text": "<b>Ex 12C · Q11</b> · If a boat travels 125 km in {2 1/2} hours, how far will it travel in 12 hours?", "opts": ["600 km", "26 km", "300 km", "1500 km"], "correct": 0, "tag": "", "sol": "Speed = 125 ÷ {5/2} = 50 km/h; in 12 hours 50 × 12 = 600 km."}]}, {"id": "s4", "label": "12.4 Inverse variation", "sub": "x × y constant; direct or inverse variation?", "slides": [{"kind": "blank", "p": "<b>Example 12</b> · If x varies inversely as y and x = 6 when y = 6, find x when y = 9.", "tag": "", "marks": "", "flat": [{"t": "x₁ : x₂ :: y₂ : y₁ gives 6 : x :: 9 : 6, so 9x = __B1__", "a": {"B1": "36"}}, {"t": "x = __B1__", "a": {"B1": "4"}}], "sol": "Product of means 9x = product of extremes 6 × 6 = 36.\nx = 36 ÷ 9 = 4; so 6 : 4 :: 9 : 6."}, {"kind": "mcq", "text": "<b>Example 13(a)</b> · State whether this is a direct or an inverse variation, and write a proportion.", "opts": ["Inverse; 4 : 7 :: 42 : 24", "Inverse; 4 : 7 :: 24 : 42", "Direct; 4 : 7 :: 24 : 42", "Direct; 4 : 24 :: 42 : 7"], "correct": 2, "tag": "", "sol": "y ÷ x = 6 in every column, so x₁/x₂ = y₁/y₂: a direct variation. Taking the pairs (4, 24) and (7, 42): {4/7} = {24/42}, so 4 : 7 :: 24 : 42.", "fig": "<svg class=\"figsvg\" viewBox=\"0 0 267 62\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><rect x=\"4.0\" y=\"4\" width=\"28.0\" height=\"26\" style=\"fill:var(--paper-2);stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"18.0\" y=\"18.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">x</text><rect x=\"32.0\" y=\"4\" width=\"28.0\" height=\"26\" style=\"fill:none;stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"46.0\" y=\"18.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">1</text><rect x=\"60.0\" y=\"4\" width=\"29.0\" height=\"26\" style=\"fill:none;stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"74.5\" y=\"18.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">2</text><rect x=\"89.0\" y=\"4\" width=\"29.0\" height=\"26\" style=\"fill:none;stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"103.5\" y=\"18.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">3</text><rect x=\"118.0\" y=\"4\" width=\"29.0\" height=\"26\" style=\"fill:none;stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"132.5\" y=\"18.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">4</text><rect x=\"147.0\" y=\"4\" width=\"29.0\" height=\"26\" style=\"fill:none;stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"161.5\" y=\"18.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">5</text><rect x=\"176.0\" y=\"4\" width=\"29.0\" height=\"26\" style=\"fill:none;stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"190.5\" y=\"18.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">6</text><rect x=\"205.0\" y=\"4\" width=\"29.0\" height=\"26\" style=\"fill:none;stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"219.5\" y=\"18.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">7</text><rect x=\"234.0\" y=\"4\" width=\"29.0\" height=\"26\" style=\"fill:none;stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"248.5\" y=\"18.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">8</text><rect x=\"4.0\" y=\"30\" width=\"28.0\" height=\"26\" style=\"fill:var(--paper-2);stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"18.0\" y=\"44.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">y</text><rect x=\"32.0\" y=\"30\" width=\"28.0\" height=\"26\" style=\"fill:none;stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"46.0\" y=\"44.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">6</text><rect x=\"60.0\" y=\"30\" width=\"29.0\" height=\"26\" style=\"fill:none;stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"74.5\" y=\"44.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">12</text><rect x=\"89.0\" y=\"30\" width=\"29.0\" height=\"26\" style=\"fill:none;stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"103.5\" y=\"44.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">18</text><rect x=\"118.0\" y=\"30\" width=\"29.0\" height=\"26\" style=\"fill:none;stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"132.5\" y=\"44.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">24</text><rect x=\"147.0\" y=\"30\" width=\"29.0\" height=\"26\" style=\"fill:none;stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"161.5\" y=\"44.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">30</text><rect x=\"176.0\" y=\"30\" width=\"29.0\" height=\"26\" style=\"fill:none;stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"190.5\" y=\"44.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">36</text><rect x=\"205.0\" y=\"30\" width=\"29.0\" height=\"26\" style=\"fill:none;stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"219.5\" y=\"44.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">42</text><rect x=\"234.0\" y=\"30\" width=\"29.0\" height=\"26\" style=\"fill:none;stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"248.5\" y=\"44.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">48</text></svg>"}, {"kind": "blank", "p": "<b>Example 13(b)</b> · State whether this is a direct or an inverse variation, and write a proportion.", "tag": "", "marks": "", "flat": [{"t": "The variation is __B1__", "a": {"B1": "inverse"}, "expr": "words", "accept": ["inverse variation"]}, {"t": "x × y = __B1__ in every column", "a": {"B1": "100"}}, {"t": "Using (2, 50) and (5, 20): 2 : 5 :: 20 : __B1__", "a": {"B1": "50"}}], "sol": "As x increases, y decreases and the product stays the same.\n1 × 100 = 2 × 50 = 4 × 25 = 5 × 20 = 10 × 10 = 100.\nx₁ : x₂ :: y₂ : y₁ gives 2 : 5 :: 20 : 50, and {2/5} = {20/50}.", "fig": "<svg class=\"figsvg\" viewBox=\"0 0 188 62\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><rect x=\"4.0\" y=\"4\" width=\"28.0\" height=\"26\" style=\"fill:var(--paper-2);stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"18.0\" y=\"18.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">x</text><rect x=\"32.0\" y=\"4\" width=\"36.5\" height=\"26\" style=\"fill:none;stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"50.2\" y=\"18.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">1</text><rect x=\"68.5\" y=\"4\" width=\"29.0\" height=\"26\" style=\"fill:none;stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"83.0\" y=\"18.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">2</text><rect x=\"97.5\" y=\"4\" width=\"29.0\" height=\"26\" style=\"fill:none;stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"112.0\" y=\"18.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">4</text><rect x=\"126.5\" y=\"4\" width=\"29.0\" height=\"26\" style=\"fill:none;stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"141.0\" y=\"18.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">5</text><rect x=\"155.5\" y=\"4\" width=\"29.0\" height=\"26\" style=\"fill:none;stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"170.0\" y=\"18.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">10</text><rect x=\"4.0\" y=\"30\" width=\"28.0\" height=\"26\" style=\"fill:var(--paper-2);stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"18.0\" y=\"44.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">y</text><rect x=\"32.0\" y=\"30\" width=\"36.5\" height=\"26\" style=\"fill:none;stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"50.2\" y=\"44.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">100</text><rect x=\"68.5\" y=\"30\" width=\"29.0\" height=\"26\" style=\"fill:none;stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"83.0\" y=\"44.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">50</text><rect x=\"97.5\" y=\"30\" width=\"29.0\" height=\"26\" style=\"fill:none;stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"112.0\" y=\"44.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">25</text><rect x=\"126.5\" y=\"30\" width=\"29.0\" height=\"26\" style=\"fill:none;stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"141.0\" y=\"44.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">20</text><rect x=\"155.5\" y=\"30\" width=\"29.0\" height=\"26\" style=\"fill:none;stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"170.0\" y=\"44.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">10</text></svg>"}, {"kind": "blank", "p": "<b>Try This</b> · If x and y are inversely proportional, find the missing quantities in the table.", "tag": "", "marks": "", "flat": [{"t": "x when y = 4: __B1__", "a": {"B1": "21"}}, {"t": "y when x = 14: __B1__", "a": {"B1": "6"}}, {"t": "x when y = 2: __B1__", "a": {"B1": "42"}}], "sol": "x × y = 7 × 12 = 84. 84 ÷ 4 = 21.\n84 ÷ 14 = 6.\n84 ÷ 2 = 42.", "fig": "<svg class=\"figsvg\" viewBox=\"0 0 150 62\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><rect x=\"4.0\" y=\"4\" width=\"28.0\" height=\"26\" style=\"fill:var(--paper-2);stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"18.0\" y=\"18.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">x</text><rect x=\"32.0\" y=\"4\" width=\"29.0\" height=\"26\" style=\"fill:none;stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"46.5\" y=\"18.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">7</text><rect x=\"61.0\" y=\"4\" width=\"28.0\" height=\"26\" style=\"fill:none;stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"75.0\" y=\"18.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">?</text><rect x=\"89.0\" y=\"4\" width=\"29.0\" height=\"26\" style=\"fill:none;stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"103.5\" y=\"18.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">14</text><rect x=\"118.0\" y=\"4\" width=\"28.0\" height=\"26\" style=\"fill:none;stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"132.0\" y=\"18.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">?</text><rect x=\"4.0\" y=\"30\" width=\"28.0\" height=\"26\" style=\"fill:var(--paper-2);stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"18.0\" y=\"44.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">y</text><rect x=\"32.0\" y=\"30\" width=\"29.0\" height=\"26\" style=\"fill:none;stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"46.5\" y=\"44.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">12</text><rect x=\"61.0\" y=\"30\" width=\"28.0\" height=\"26\" style=\"fill:none;stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"75.0\" y=\"44.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">4</text><rect x=\"89.0\" y=\"30\" width=\"29.0\" height=\"26\" style=\"fill:none;stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"103.5\" y=\"44.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">?</text><rect x=\"118.0\" y=\"30\" width=\"28.0\" height=\"26\" style=\"fill:none;stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"132.0\" y=\"44.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">2</text></svg>"}, {"kind": "mcq", "text": "<b>Ex 12D · Q1(a–c)</b> · State which of these are direct and which are inverse variations.", "opts": ["a) direct  b) direct  c) direct", "a) direct  b) inverse  c) inverse", "a) inverse  b) direct  c) direct", "a) direct  b) direct  c) inverse"], "correct": 3, "tag": "", "sol": "a) y ÷ x = 3 every time: direct. b) y ÷ x = {10/3} every time: direct. c) x × y = 120 every time: inverse.", "fig": "<div class=\"tscroll\"><table class=\"ttab\"><tr><th rowspan=\"2\">a)</th><th>x</th><td>3</td><td>4</td><td>8</td><td>1</td><td>6</td><td>7</td></tr><tr><th>y</th><td>9</td><td>12</td><td>24</td><td>3</td><td>18</td><td>21</td></tr><tr><th rowspan=\"2\">b)</th><th>x</th><td>3</td><td>6</td><td>9</td><td>12</td><td>15</td><td>18</td></tr><tr><th>y</th><td>10</td><td>20</td><td>30</td><td>40</td><td>50</td><td>60</td></tr><tr><th rowspan=\"2\">c)</th><th>x</th><td>10</td><td>5</td><td>8</td><td>4</td><td>20</td><td>40</td><td>1</td></tr><tr><th>y</th><td>12</td><td>24</td><td>15</td><td>30</td><td>6</td><td>3</td><td>120</td></tr></table></div>"}, {"kind": "mcq", "text": "<b>Ex 12D · Q1(d–f)</b> · State which of these are direct and which are inverse variations.", "opts": ["d) inverse  e) direct  f) inverse", "d) inverse  e) direct  f) direct", "d) direct  e) direct  f) inverse", "d) inverse  e) inverse  f) direct"], "correct": 0, "tag": "", "sol": "d) x × y = 150 every time: inverse. e) y ÷ x = 1.5 every time: direct. f) x × y = 90 every time (0.9 × 100 = 90): inverse.", "fig": "<div class=\"tscroll\"><table class=\"ttab\"><tr><th rowspan=\"2\">d)</th><th>x</th><td>30</td><td>50</td><td>10</td><td>2</td><td>3</td><td>15</td></tr><tr><th>y</th><td>5</td><td>3</td><td>15</td><td>75</td><td>50</td><td>10</td></tr><tr><th rowspan=\"2\">e)</th><th>x</th><td>2</td><td>3</td><td>4</td><td>7</td><td>8</td><td>10</td></tr><tr><th>y</th><td>3</td><td>4.5</td><td>6</td><td>10.5</td><td>12</td><td>15</td></tr><tr><th rowspan=\"2\">f)</th><th>x</th><td>3</td><td>45</td><td>10</td><td>6</td><td>15</td><td>0.9</td></tr><tr><th>y</th><td>30</td><td>2</td><td>9</td><td>15</td><td>6</td><td>100</td></tr></table></div>"}, {"kind": "blank", "p": "<b>Ex 12D · Q2(a–c)</b> · x varies inversely as y.", "tag": "", "marks": "", "flat": [{"t": "a) x = 10 when y = 8; find y when x = 4: y = __B1__", "a": {"B1": "20"}}, {"t": "b) x = 9 when y = 21; find x when y = 7: x = __B1__", "a": {"B1": "27"}}, {"t": "c) x = 12 when y = 33; find x when y = 11: x = __B1__", "a": {"B1": "36"}}], "sol": "xy = 80, so y = 80 ÷ 4 = 20.\nxy = 189, so x = 189 ÷ 7 = 27.\nxy = 396, so x = 396 ÷ 11 = 36."}, {"kind": "blank", "p": "<b>Ex 12D · Q2(d–f)</b> · Inverse variation.", "tag": "", "marks": "", "flat": [{"t": "d) x varies inversely as y and x = {1/2} when y is 16; find y when x = 4: y = __B1__", "a": {"B1": "2"}}, {"t": "e) x varies inversely as y and x = 3 when y = 20; find x when y is 5: x = __B1__", "a": {"B1": "12"}}, {"t": "f) x varies inversely as y<sup>2</sup> and x = 3 when y = 4; find x when y = 2: x = __B1__", "a": {"B1": "12"}}], "sol": "xy = {1/2} × 16 = 8, so y = 8 ÷ 4 = 2.\nxy = 60, so x = 60 ÷ 5 = 12.\nx × y<sup>2</sup> = 3 × 16 = 48; y<sup>2</sup> = 4, so x = 48 ÷ 4 = 12."}, {"kind": "mcq", "text": "<b>Ex 12D · Q3(a–d)</b> · Identify the direct and inverse variations:  a) number of people and the time to complete a piece of work  b) number of people and the number of days to consume a given quantity of food  c) time taken to travel a given distance if speed is changing  d) number of people and quantity of food", "opts": ["a) direct  b) inverse  c) inverse  d) direct", "a) inverse  b) inverse  c) direct  d) inverse", "a) inverse  b) inverse  c) inverse  d) direct", "a) inverse  b) direct  c) inverse  d) direct"], "correct": 2, "tag": "", "sol": "a) More people take less time: inverse. b) More people finish the food in fewer days: inverse. c) For a given distance, a higher speed means less time: inverse. d) More people need more food: direct."}, {"kind": "mcq", "text": "<b>Ex 12D · Q3(e–g)</b> · Identify the direct and inverse variations:  e) the time taken and distance travelled when the speed is constant  f) increase in cost and number of articles that can be purchased if the budget remains the same  g) number of articles purchased and total cost", "opts": ["e) inverse  f) inverse  g) direct", "e) direct  f) direct  g) direct", "e) direct  f) inverse  g) inverse", "e) direct  f) inverse  g) direct"], "correct": 3, "tag": "", "sol": "e) At a constant speed, more time means more distance: direct. f) With a fixed budget, a higher price buys fewer articles: inverse. g) More articles cost more: direct."}]}, {"id": "s5", "label": "12.5 Inverse proportion problems", "sub": "Workers, food supplies, speed and time; problems with three variables", "slides": [{"kind": "blank", "p": "<b>Example 14</b> · Rajan has enough money to buy 30 books at the rate of ₹20 per book. If the price of each book is increased to ₹25, how many books can Rajan buy with the same amount of money?", "tag": "", "marks": "", "flat": [{"t": "20 : 25 :: y : 30, so 25y = __B1__", "a": {"B1": "600"}}, {"t": "Books = __B1__", "a": {"B1": "24"}}], "sol": "Price up, books down: inverse. Product of means 25y = product of extremes 20 × 30 = 600.\ny = 600 ÷ 25 = 24 books."}, {"kind": "mcq", "text": "<b>Example 15</b> · In an army camp, there are 800 soldiers. There is enough food for them for 60 days. If 400 more soldiers arrive at the camp, how many days will the food last?", "opts": ["90 days", "30 days", "40 days", "120 days"], "correct": 2, "tag": "", "sol": "Soldiers now = 1200. Inverse: 800 : 1200 :: x : 60, so 1200x = 60 × 800 = 48000 and x = 40 days."}, {"kind": "blank", "p": "<b>Example 16</b> · Mr Gupta drives at a speed of 60 km/h for 6 hours from Chandigarh to Delhi. Mr Verma drives his car at an average speed of 45 km/h for the same journey. How much time does Mr Verma take?", "tag": "", "marks": "", "flat": [{"t": "Time = __B1__ hours", "a": {"B1": "8"}}], "sol": "Lower speed, more time: inverse. 60 : 45 :: x : 6, so 45x = 360 and x = 8 hours."}, {"kind": "blank", "p": "<b>Example 17</b> · A hostel spends ₹3200 as cost of rice for 20 students for 30 days. If they spend ₹2400 for 30 students, for how many days will the rice last?", "tag": "", "marks": "", "flat": [{"t": "Step 1 (money fixed at ₹3200): 30 students, days = __B1__", "a": {"B1": "20"}}, {"t": "Step 2 (30 students): ₹2400 lasts __B1__ days", "a": {"B1": "15"}}], "sol": "Students and days vary inversely: 30 : 20 :: 30 : x, 30x = 600, x = 20 days.\nMoney and days vary directly: 3200 : 2400 :: 20 : x, 3200x = 48000, x = 15 days.", "fig": "<svg class=\"figsvg\" viewBox=\"0 0 177 88\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><rect x=\"4.0\" y=\"4\" width=\"81.5\" height=\"26\" style=\"fill:var(--paper-2);stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"44.8\" y=\"18.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">Students</text><rect x=\"85.5\" y=\"4\" width=\"44.0\" height=\"26\" style=\"fill:none;stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"107.5\" y=\"18.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">20</text><rect x=\"129.5\" y=\"4\" width=\"44.0\" height=\"26\" style=\"fill:none;stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"151.5\" y=\"18.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">30</text><rect x=\"4.0\" y=\"30\" width=\"81.5\" height=\"26\" style=\"fill:var(--paper-2);stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"44.8\" y=\"44.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">Money (₹)</text><rect x=\"85.5\" y=\"30\" width=\"44.0\" height=\"26\" style=\"fill:none;stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"107.5\" y=\"44.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">3200</text><rect x=\"129.5\" y=\"30\" width=\"44.0\" height=\"26\" style=\"fill:none;stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"151.5\" y=\"44.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">2400</text><rect x=\"4.0\" y=\"56\" width=\"81.5\" height=\"26\" style=\"fill:var(--paper-2);stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"44.8\" y=\"70.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">Days</text><rect x=\"85.5\" y=\"56\" width=\"44.0\" height=\"26\" style=\"fill:none;stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"107.5\" y=\"70.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">30</text><rect x=\"129.5\" y=\"56\" width=\"44.0\" height=\"26\" style=\"fill:none;stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"151.5\" y=\"70.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">x</text></svg>"}, {"kind": "mcq", "text": "<b>Try This · Q1</b> · If 15 men can do a piece of work in 7 days, in how many days can 21 men do the work?", "opts": ["3 days", "5 days", "10 days", "9.8 days"], "correct": 1, "tag": "", "sol": "Inverse: 15 × 7 = 105 man-days; 105 ÷ 21 = 5 days."}, {"kind": "blank", "p": "<b>Try This · Q2</b> · There are 50 soldiers in a military camp. Food provision for them is for 12 days. How long will these provisions last if 10 more soldiers join the camp?", "tag": "", "marks": "", "flat": [{"t": "Days = __B1__", "a": {"B1": "10"}}], "sol": "60 soldiers: 50 × 12 = 60 × x, so x = 600 ÷ 60 = 10 days."}, {"kind": "mcq", "text": "<b>Ex 12E · Q1</b> · A piece of work can be completed by 45 men in 90 days. If only 30 men are available, how many days will it take to complete the same work?", "opts": ["120 days", "75 days", "135 days", "60 days"], "correct": 2, "tag": "", "sol": "Fewer men, more days: 45 × 90 = 30 × x, so x = 4050 ÷ 30 = 135 days."}, {"kind": "blank", "p": "<b>Ex 12E · Q2</b> · A college hostel with 320 students has a stock of food for 80 days. If 20 students leave the hostel after 20 days, for how many more days will the food last?", "tag": "", "marks": "", "flat": [{"t": "After 20 days the food left would last 320 students for __B1__ days", "a": {"B1": "60"}}, {"t": "Students remaining = __B1__", "a": {"B1": "300"}}, {"t": "The food will last __B1__ more days", "a": {"B1": "64"}}], "sol": "80 − 20 = 60 days of food remain for 320 students.\n320 − 20 = 300 students.\n320 × 60 = 300 × x, so x = 19200 ÷ 300 = 64 days."}, {"kind": "blank", "p": "<b>Ex 12E · Q3</b> · One gas cylinder is used to cook food for a family of 8 people for 30 days. If 4 guests join the family, how long will the cylinder last?", "tag": "", "marks": "", "flat": [{"t": "The cylinder will last __B1__ days", "a": {"B1": "20"}}], "sol": "12 people: 8 × 30 = 12 × x, so x = 240 ÷ 12 = 20 days."}, {"kind": "mcq", "text": "<b>Ex 12E · Q4</b> · Five tractors can mow a field in 8 days. If there are only 4 tractors available, in how many days will the field be mowed?", "opts": ["6.4 days", "32 days", "10 days", "9 days"], "correct": 2, "tag": "", "sol": "5 × 8 = 4 × x, so x = 40 ÷ 4 = 10 days."}, {"kind": "blank", "p": "<b>Ex 12E · Q5</b> · A car travels for 8 hours at an average speed of 60 km/h. If the car keeps up an average speed of 48 km/h, how long will it take to complete the same journey?", "tag": "", "marks": "", "flat": [{"t": "Time = __B1__ hours", "a": {"B1": "10"}}], "sol": "Same distance (480 km): 60 × 8 = 48 × x, so x = 10 hours."}, {"kind": "blank", "p": "<b>Ex 12E · Q6</b> · A family of 8 people have enough stock of rice to last for 30 days. Due to the arrival of some relatives, this food was consumed in 20 days. How many guests joined the family?", "tag": "", "marks": "", "flat": [{"t": "People eating = __B1__", "a": {"B1": "12"}}, {"t": "Guests = __B1__", "a": {"B1": "4"}}], "sol": "8 × 30 = x × 20, so x = 240 ÷ 20 = 12 people.\n12 − 8 = 4 guests."}, {"kind": "mcq", "text": "<b>Ex 12E · Q7</b> · From a roll of curtain cloth, 9 curtains each of length 4 metres can be cut. If the curtains needed are 3 metres long, how many curtains can be made out of this cloth?", "opts": ["27", "7", "10", "12"], "correct": 3, "tag": "", "sol": "Cloth = 9 × 4 = 36 m; 36 ÷ 3 = 12 curtains (length and number vary inversely)."}, {"kind": "blank", "p": "<b>Ex 12E · Q8</b> · A train can finish a journey in 10 hours travelling at a speed of 56 km/h. If another faster train is to cover the same journey in 8 hours, what should be the speed of the new train?", "tag": "", "marks": "", "flat": [{"t": "Speed = __B1__ km/h", "a": {"B1": "70"}}], "sol": "Distance = 56 × 10 = 560 km; 560 ÷ 8 = 70 km/h."}, {"kind": "blank", "p": "<b>Ex 12E · Q9</b> · Working 5 hours daily, Shaheed can embroider 3 sarees in 21 days. How many days will it take for him to embroider 6 sarees working 7 hours daily?", "tag": "", "marks": "", "flat": [{"t": "Hours for 3 sarees = __B1__", "a": {"B1": "105"}}, {"t": "Hours for 6 sarees = __B1__", "a": {"B1": "210"}}, {"t": "Days at 7 hours daily = __B1__", "a": {"B1": "30"}}], "sol": "5 × 21 = 105 hours for 3 sarees.\n6 sarees need twice as long: 210 hours (direct).\n210 ÷ 7 = 30 days (hours per day and days vary inversely)."}, {"kind": "mcq", "text": "<b>Ex 12E · Q10</b> · If 6 workers earn ₹10,800 in 15 days, how much will 12 workers earn in 8 days?", "opts": ["₹43,200", "₹11,520", "₹10,800", "₹5760"], "correct": 1, "tag": "", "sol": "One worker earns 10800 ÷ (6 × 15) = ₹120 a day. 12 workers × 8 days × ₹120 = ₹11,520."}, {"kind": "blank", "p": "<b>Ex 12E · Q11</b> · Ten men working for 5 hours a day for 6 days mow an area of 5 acres. If there are 8 men working 4 hours a day to mow 4 acres of land, how many days will it take?", "tag": "", "marks": "", "flat": [{"t": "Man-hours for 5 acres = __B1__", "a": {"B1": "300"}}, {"t": "Man-hours for 4 acres = __B1__", "a": {"B1": "240"}}, {"t": "Days = __B1__", "a": {"B1": "15/2"}, "expr": "fv"}], "sol": "10 × 5 × 6 = 300 man-hours.\n300 ÷ 5 = 60 per acre; 4 acres need 240 man-hours.\n8 men × 4 hours = 32 man-hours a day; 240 ÷ 32 = 7.5 days."}, {"kind": "mcq", "text": "<b>Ex 12E · Q12</b> · Given that 12 workers can do a piece of work in 16 days. If 12 more workers are added to the workforce, in how many days will they complete the work?", "opts": ["12 days", "4 days", "32 days", "8 days"], "correct": 3, "tag": "", "sol": "24 workers: 12 × 16 = 24 × x, so x = 8 days (twice the workers, half the time)."}, {"kind": "blank", "p": "<b>Ex 12E · Q13</b> · A total of 20 men can complete the construction of a road in 30 days. If 5 more men join the team, in how many days will the work be over?", "tag": "", "marks": "", "flat": [{"t": "Days = __B1__", "a": {"B1": "24"}}], "sol": "25 men: 20 × 30 = 25 × x, so x = 600 ÷ 25 = 24 days."}]}, {"id": "s6", "label": "12.6 Time and work", "sub": "One day’s work, working together, pipes and leaks", "slides": [{"kind": "blank", "p": "<b>Example 18</b> · Satish can paint a house in 6 days, while Ritesh takes 12 days to do it alone. If both of them work together, how long will they take to paint the house?", "tag": "", "marks": "", "flat": [{"t": "Work in one day together = __B1__ of the house", "a": {"B1": "1/4"}, "expr": "fl"}, {"t": "Days together = __B1__", "a": {"B1": "4"}}], "sol": "{1/6} + {1/12} = (2 + 1)/12 = {3/12} = {1/4}.\n1 ÷ {1/4} = 4 days."}, {"kind": "mcq", "text": "<b>Example 19</b> · A water tank has three inlets. Inlet 1 alone can fill the tank in 30 minutes, inlet 2 in 40 minutes and inlet 3 in 60 minutes. If all three inlets are opened together, how long will it take to fill the tank?", "opts": ["13 min 20 s", "10 min", "43 min 20 s", "130 min"], "correct": 0, "tag": "", "sol": "One minute: {1/30} + {1/40} + {1/60} = (4 + 3 + 2)/120 = {9/120}. Time = {120/9} = {40/3} = {13 1/3} minutes = 13 min 20 s."}, {"kind": "blank", "p": "<b>Try This · Q1</b> · A alone can do a piece of work in 7 days and B alone can do the work in 8 days. If both of them work together, how long will they take to complete the work?", "tag": "", "marks": "", "flat": [{"t": "One day’s work together = __B1__", "a": {"B1": "15/56"}, "expr": "fl"}, {"t": "Time = __B1__ days", "a": {"B1": "56/15"}, "expr": "fl"}], "sol": "{1/7} + {1/8} = (8 + 7)/56 = {15/56}.\n1 ÷ {15/56} = {56/15} = {3 11/15} days."}, {"kind": "mcq", "text": "<b>Try This · Q2</b> · A tank can be filled up by a tap in 2 hours. Due to a leak in its bottom, the tap fills it up in 5 hours. If the tank is full, in how much time will it be emptied by the leak?", "opts": ["7 h", "3 h", "1 h 26 min", "3 h 20 min"], "correct": 3, "tag": "", "sol": "Leak per hour = {1/2} − {1/5} = {3/10} of the tank. Time = {10/3} h = 3 h 20 min."}, {"kind": "blank", "p": "<b>Ex 12F · Q1</b> · A water tank has an inlet and an outlet. The inlet can fill the tank in 20 minutes and the outlet can empty it in 40 minutes. Both are open while the empty tank is being filled. In how much time will the tank be just filled?", "tag": "", "marks": "", "flat": [{"t": "Part filled per minute = __B1__", "a": {"B1": "1/40"}, "expr": "fl"}, {"t": "Time = __B1__ minutes", "a": {"B1": "40"}}], "sol": "{1/20} − {1/40} = {1/40} of the tank.\n1 ÷ {1/40} = 40 minutes."}, {"kind": "mcq", "text": "<b>Ex 12F · Q2</b> · Jaya and Seema can together do a piece of work in 10 hours. Seema alone can do it in 15 hours. How long will Jaya take to do it alone?", "opts": ["6 hours", "25 hours", "5 hours", "30 hours"], "correct": 3, "tag": "", "sol": "Jaya’s one hour = {1/10} − {1/15} = (3 − 2)/30 = {1/30}, so she takes 30 hours."}, {"kind": "blank", "p": "<b>Ex 12F · Q3</b> · Three pumps of the same capacity can fill a swimming pool in 15 hours. How long will it take for 5 pumps of the same capacity to fill the pool?", "tag": "", "marks": "", "flat": [{"t": "Time = __B1__ hours", "a": {"B1": "9"}}], "sol": "More pumps, less time: 3 × 15 = 5 × x, x = 9 hours."}, {"kind": "blank", "p": "<b>Ex 12F · Q4</b> · Saleem can type 30 words per minute and Ranjit can type 50 words per minute. If Saleem needs 30 minutes to finish typing a piece of work, how long will Ranjit take to finish the same work?", "tag": "", "marks": "", "flat": [{"t": "Words in the work = __B1__", "a": {"B1": "900"}}, {"t": "Ranjit’s time = __B1__ minutes", "a": {"B1": "18"}}], "sol": "30 × 30 = 900 words.\n900 ÷ 50 = 18 minutes."}, {"kind": "mcq", "text": "<b>Ex 12F · Q5</b> · A alone can do a piece of work in 8 days. A and B together can finish the same work in 6 days. If B alone is doing the work, how long will he take?", "opts": ["2 days", "14 days", "24 days", "48 days"], "correct": 2, "tag": "", "sol": "B’s one day = {1/6} − {1/8} = (4 − 3)/24 = {1/24}, so B takes 24 days."}, {"kind": "blank", "p": "<b>Ex 12F · Q6</b> · 10 masons can build a wall working 7 hours a day in 12 days. In how many days can the work be completed by 14 persons working 8 hours a day?", "tag": "", "marks": "", "flat": [{"t": "Total person-hours = __B1__", "a": {"B1": "840"}}, {"t": "Days = __B1__", "a": {"B1": "15/2"}, "expr": "fv"}], "sol": "10 × 7 × 12 = 840 person-hours.\n14 × 8 = 112 person-hours a day; 840 ÷ 112 = 7.5 days."}]}, {"id": "s7", "label": "12.7 Time and distance", "sub": "Speed, km/h and m/s, trains crossing posts, bridges and platforms", "slides": [{"kind": "blank", "p": "<b>Example 20</b> · A train of length 375 m travels at a speed of 45 km/h. How long will it take to pass a signal post?", "tag": "", "marks": "", "flat": [{"t": "Distance to cover = __B1__ m", "a": {"B1": "375"}}, {"t": "Time = __B1__ s", "a": {"B1": "30"}}], "sol": "To pass a post the train covers its own length, 375 m.\n45000 m take 3600 s, so 375 m take 3600 × 375 ÷ 45000 = 30 s."}, {"kind": "mcq", "text": "<b>Example 21</b> · A train of length 350 m crosses a bridge of length 750 m. If the speed of the train is 55 km/h, how much time will the train take to cross the bridge?", "opts": ["72 s", "23 s", "1 min 50 s", "49 s"], "correct": 0, "tag": "", "sol": "Distance = 750 + 350 = 1100 m. 55000 m take 3600 s, so 1100 m take 1100 × 3600 ÷ 55000 = 72 s."}, {"kind": "blank", "p": "<b>Try This · Q1</b> · A train, 160 m long, is running at 40 km/h. In how much time will it pass a platform that is 140 m long?", "tag": "", "marks": "", "flat": [{"t": "Distance = __B1__ m", "a": {"B1": "300"}}, {"t": "Time = __B1__ s", "a": {"B1": "27"}}], "sol": "160 + 140 = 300 m.\n40 km/h = 40000 m per 3600 s; 300 × 3600 ÷ 40000 = 27 s."}, {"kind": "mcq", "text": "<b>Try This · Q2</b> · A car travels 70 km in 30 minutes. Find its speed in km/h.", "opts": ["140 km/h", "2100 km/h", "70 km/h", "35 km/h"], "correct": 0, "tag": "", "sol": "30 minutes = {1/2} h; 70 ÷ {1/2} = 140 km/h."}, {"kind": "blank", "p": "<b>Ex 12G · Q1</b> · The distance between two cities A and B is 425 km. If a car leaves city A at 2 p.m. and reaches city B at 10.30 p.m., what is the speed of the car? (The book prints “10.30 a.m.”; the same-day arrival 10.30 p.m. is meant.)", "tag": "", "marks": "", "flat": [{"t": "Time taken = __B1__ hours", "a": {"B1": "17/2"}, "expr": "fv"}, {"t": "Speed = __B1__ km/h", "a": {"B1": "50"}}], "sol": "2 p.m. to 10.30 p.m. is 8 h 30 min = 8.5 h.\n425 ÷ 8.5 = 50 km/h."}, {"kind": "mcq", "text": "<b>Ex 12G · Q2</b> · In 8 minutes, Rajan jogs 800 metres. What is his speed in km/h?", "opts": ["10 km/h", "100 km/h", "0.1 km/h", "6 km/h"], "correct": 3, "tag": "", "sol": "800 m = 0.8 km and 8 min = {8/60} h. Speed = 0.8 × {60/8} = 6 km/h (100 m per minute = 6000 m per hour)."}, {"kind": "blank", "p": "<b>Ex 12G · Q3</b> · A car travels 60 km in 45 minutes. Find its speed in km/hour.", "tag": "", "marks": "", "flat": [{"t": "Speed = __B1__ km/h", "a": {"B1": "80"}}], "sol": "45 min = {3/4} h; 60 ÷ {3/4} = 80 km/h."}, {"kind": "mcq", "text": "<b>Ex 12G · Q4</b> · Mr Jain drives a distance of 420 km at a speed of 60 km/h. In how much time does he complete the journey?", "opts": ["6 hours", "8 hours", "7 h 30 min", "7 hours"], "correct": 3, "tag": "", "sol": "Time = 420 ÷ 60 = 7 hours."}, {"kind": "blank", "p": "<b>Ex 12G · Q5</b> · A train travels a distance of 540 km in 9 hours. How much time will this train take to travel 330 km?", "tag": "", "marks": "", "flat": [{"t": "Speed = __B1__ km/h", "a": {"B1": "60"}}, {"t": "Time = __B1__ hours", "a": {"B1": "11/2"}, "expr": "fv"}], "sol": "540 ÷ 9 = 60 km/h.\n330 ÷ 60 = 5.5 hours = 5 h 30 min."}, {"kind": "blank", "p": "<b>Ex 12G · Q6</b> · A train running at a speed of 45 km/h is 400 m long. How long will it take to pass a vendor standing on the station platform?", "tag": "", "marks": "", "flat": [{"t": "45 km/h = __B1__ m/s", "a": {"B1": "25/2"}, "expr": "fv"}, {"t": "Time = __B1__ s", "a": {"B1": "32"}}], "sol": "45 × {5/18} = 12.5 m/s.\nTo pass a standing person the train covers its own length: 400 ÷ 12.5 = 32 s."}, {"kind": "mcq", "text": "<b>Ex 12G · Q7</b> · At 7 a.m. Lalit starts his journey from Delhi on his car to Nainital, 285 kilometres away. He drives at a speed of 30 km/h. At what time will he reach his destination?", "opts": ["4.30 p.m.", "9.30 a.m.", "5.30 p.m.", "4.30 a.m."], "correct": 0, "tag": "", "sol": "Time = 285 ÷ 30 = 9.5 h = 9 h 30 min. 7 a.m. + 9 h 30 min = 4.30 p.m."}]}, {"id": "s8", "label": "Assessment A", "sub": "Knowing and understanding", "slides": [{"kind": "mcq", "text": "<b>Check-up · MCQ 1</b> · Which of the following vary inversely with each other?", "opts": ["distance covered and taxi fare", "distance travelled and time taken", "speed and distance covered", "speed and time taken"], "correct": 3, "tag": "", "sol": "For a fixed distance, a higher speed means less time: speed × time = distance is constant. The other pairs increase together (direct)."}, {"kind": "mcq", "text": "<b>Check-up · MCQ 2</b> · If x and y are inversely proportional then ______ = k, where k is a positive constant.", "opts": ["x ÷ y", "x − y", "xy", "x + y"], "correct": 2, "tag": "", "sol": "In inverse proportion the product xy stays constant."}, {"kind": "blank", "p": "<b>Check-up · Q3(a–c)</b> · Complete the equivalent ratios.", "tag": "", "marks": "", "flat": [{"t": "a) {1/3} = 2 ÷ □ = 3 ÷ □ = □ ÷ 12: the boxes are __B1__, __B2__, __B3__", "a": {"B1": "6", "B2": "9", "B3": "4"}}, {"t": "b) {3/5} = 6 ÷ □ = 9 ÷ □ = □ ÷ 20: the boxes are __B1__, __B2__, __B3__", "a": {"B1": "10", "B2": "15", "B3": "12"}}, {"t": "c) {1/8} = 7 ÷ □: □ = __B1__", "a": {"B1": "56"}}], "sol": "Multiply the top and bottom by 2, 3 and 4: {2/6}, {3/9}, {4/12}.\nMultiply by 2, 3 and 4: {6/10}, {9/15}, {12/20}.\nMultiply by 7: {7/56}."}, {"kind": "blank", "p": "<b>Check-up · Q3(d–f)</b> · Complete the equivalent ratios.", "tag": "", "marks": "", "flat": [{"t": "d) {13/40} = 39 ÷ □: □ = __B1__", "a": {"B1": "120"}}, {"t": "e) {5/6} = □ ÷ 24: □ = __B1__", "a": {"B1": "20"}}, {"t": "f) {6/7} = □ ÷ 14 = 18 ÷ □ = □ ÷ 28: the boxes are __B1__, __B2__, __B3__", "a": {"B1": "12", "B2": "21", "B3": "24"}}], "sol": "39 = 13 × 3, so 40 × 3 = 120.\n24 = 6 × 4, so 5 × 4 = 20.\n× 2: {12/14}; × 3: {18/21}; × 4: {24/28}."}, {"kind": "mcq", "text": "<b>Check-up · Q5</b> · The number of girls and boys in a school is 525 and 675 respectively. What is the ratio of the boys to girls in its simplest form?", "opts": ["7 : 9", "9 : 7", "3 : 4", "27 : 21"], "correct": 1, "tag": "", "sol": "Boys : girls = 675 : 525; HCF 75 gives 9 : 7."}, {"kind": "blank", "p": "<b>Check-up · Q6</b> · The English textbook of Class VIII costs ₹240 and the Mathematics textbook costs ₹210. What is the ratio of the cost of the English textbook to the Mathematics textbook in its simplest form?", "tag": "", "marks": "", "flat": [{"t": "English : Maths = __B1__ : __B2__", "a": {"B1": "8", "B2": "7"}}], "sol": "240 : 210; HCF 30 gives 8 : 7."}, {"kind": "mcq", "text": "<b>Check-up · Q8</b> · If five eggs cost ₹28, how many eggs can be bought for ₹224?", "opts": ["48", "40", "8", "35"], "correct": 1, "tag": "", "sol": "224 ÷ 28 = 8, so 8 × 5 = 40 eggs."}, {"kind": "mcq", "text": "<b>Check-up · Q9</b> · The number of stamps collected by Arvind and Arshu are in the ratio 7 : 3. Together they have 180 stamps. Find the number of stamps each one has.", "opts": ["Arvind 105, Arshu 75", "Arvind 126, Arshu 54", "Arvind 140, Arshu 60", "Arvind 54, Arshu 126"], "correct": 1, "tag": "", "sol": "7 + 3 = 10 parts; one part = 18. Arvind 7 × 18 = 126, Arshu 3 × 18 = 54."}, {"kind": "blank", "p": "<b>Check-up · Q13</b> · Amarjeet earns ₹160 for three hours of work. How much will he earn for 27 hours of work?", "tag": "", "marks": "", "flat": [{"t": "Earnings = ₹__B1__", "a": {"B1": "1440"}}], "sol": "27 hours = 9 × 3 hours, so 9 × 160 = ₹1440."}, {"kind": "mcq", "text": "<b>Check-up · Q15</b> · The cost of bus tickets for 5 people for a journey was ₹95. What is the number of tickets that can be bought for ₹342 for the same journey?", "opts": ["24", "19", "18", "17"], "correct": 2, "tag": "", "sol": "One ticket = 95 ÷ 5 = ₹19; 342 ÷ 19 = 18 tickets."}]}, {"id": "s9", "label": "Assessment B", "sub": "Investigating patterns", "slides": [{"kind": "blank", "p": "<b>Check-up · Q4</b> · Direct variation with powers.", "tag": "", "marks": "", "flat": [{"t": "a) x varies directly as y<sup>2</sup>, x = 7 when y = 1; find x when y = 3: x = __B1__", "a": {"B1": "63"}}, {"t": "b) y varies directly as x<sup>2</sup>, x = 2 when y = 3; find y when x = 6: y = __B1__", "a": {"B1": "27"}}, {"t": "c) x varies directly as y<sup>3</sup>, x = 2 when y = 1; find x when y is 3: x = __B1__", "a": {"B1": "54"}}], "sol": "x ÷ y<sup>2</sup> = 7, so x = 7 × 9 = 63.\ny ÷ x<sup>2</sup> = {3/4}, so y = {3/4} × 36 = 27.\nx ÷ y<sup>3</sup> = 2, so x = 2 × 27 = 54."}, {"kind": "mcq", "text": "<b>Check-up · Q10</b> · The pocket money of Joan and Joyce are in the ratio 10 : 8. If Joan has ₹20 more than Joyce, find the pocket money of each one.", "opts": ["Joan ₹200, Joyce ₹180", "Joan ₹50, Joyce ₹30", "Joan ₹100, Joyce ₹80", "Joan ₹80, Joyce ₹100"], "correct": 2, "tag": "", "sol": "10x − 8x = 2x = 20, so x = 10. Joan 10 × 10 = ₹100, Joyce 8 × 10 = ₹80."}, {"kind": "blank", "p": "<b>Check-up · Q11</b> · Two supplementary angles (two angles whose sum is 180°) are in the ratio 5 : 1. Find the measure of each angle.", "tag": "", "marks": "", "flat": [{"t": "The angles are __B1__° and __B2__°", "a": {"B1": "150", "B2": "30"}}], "sol": "5x + x = 6x = 180°, x = 30°: the angles are 150° and 30°."}, {"kind": "blank", "p": "<b>Check-up · Q12</b> · If we divide ₹5250 in the ratio 6 : 7 : 8 among three friends Sarosh, Santosh and Rajiv, how much will each of them get?", "tag": "", "marks": "", "flat": [{"t": "Sarosh ₹__B1__, Santosh ₹__B2__, Rajiv ₹__B3__", "a": {"B1": "1500", "B2": "1750", "B3": "2000"}}], "sol": "6 + 7 + 8 = 21 parts; one part = 5250 ÷ 21 = ₹250. So ₹1500, ₹1750 and ₹2000."}, {"kind": "mcq", "text": "<b>Check-up · Brain Teaser</b> · Mona has a 2.5 in × 4.25 in picture. The printer’s standard sizes are: Regular 5.0 × 8.0, 5.0 × 8.50, 7.5 × 12.75; Medium 20.0 × 34.0, 25.0 × 40.0, 30.0 × 50.0; Large 50.5 × 85.5, 55.0 × 93.5, 62.5 × 105.0. Which sizes give perfectly enlarged, distortion-free photographs?", "opts": ["5.0 × 8.0, 25.0 × 40.0 and 62.5 × 105.0", "5.0 × 8.50, 7.5 × 12.75, 20.0 × 34.0 and 55.0 × 93.5", "5.0 × 8.50, 7.5 × 12.75 and 30.0 × 50.0", "All of the medium sizes"], "correct": 1, "tag": "", "sol": "The sides must be in the ratio 2.5 : 4.25 = 10 : 17, i.e. the long side = 1.7 × the short side. 5 × 1.7 = 8.5 ✓, 7.5 × 1.7 = 12.75 ✓, 20 × 1.7 = 34 ✓, 55 × 1.7 = 93.5 ✓. The others fail: 5 × 1.7 ≠ 8, 25 × 1.7 = 42.5 ≠ 40, 30 × 1.7 = 51 ≠ 50, 50.5 × 1.7 = 85.85 ≠ 85.5, 62.5 × 1.7 = 106.25 ≠ 105."}, {"kind": "blank", "p": "<b>Check-up · HOTS</b> · A contractor calculated that he could finish the construction of a road in 40 working days. He knew that if he appointed 32 people and made them work for 6 hours a day for 5 days in a week, the work would finish in time. But he could arrange for only 20 workers. He decided to make them work for 8 hours a day for 6 days a week. Will they complete the work in time? If not, how many more days will they take?", "tag": "", "marks": "", "flat": [{"t": "Planned time: 40 working days at 5 days a week = __B1__ weeks", "a": {"B1": "8"}}, {"t": "Planned work per week = 32 × 6 × 5 = __B1__ person-hours", "a": {"B1": "960"}}, {"t": "Work per week with 20 workers = 20 × 8 × 6 = __B1__ person-hours", "a": {"B1": "960"}}, {"t": "Total work = 32 × 6 × 40 = 7680 person-hours, so the 20 workers need __B1__ weeks", "a": {"B1": "8"}}, {"t": "Will they complete the work in time? (yes / no) __B1__", "a": {"B1": "yes"}, "expr": "words"}], "sol": "40 ÷ 5 = 8 weeks.\n32 people × 6 hours × 5 days = 960 person-hours a week.\n20 workers × 8 hours × 6 days = 960 person-hours a week: exactly the same as planned.\n7680 ÷ 960 = 8 weeks (that is 48 working days of 6 a week instead of 40 working days of 5 a week).\nYes. They finish in the same 8 weeks, so no extra days are needed."}, {"kind": "mcq", "text": "In a table x and y vary directly. If x is multiplied by 3, what happens to y?", "opts": ["y does not change", "y is divided by 3", "y is multiplied by 3", "y increases by 3"], "correct": 2, "tag": "", "sol": "y = kx, so 3x gives k(3x) = 3y."}, {"kind": "mcq", "text": "In a table x and y vary inversely. If x is doubled, what happens to y?", "opts": ["y decreases by 2", "y is halved", "y does not change", "y is doubled"], "correct": 1, "tag": "", "sol": "xy = k, so (2x) × ({y/2}) = xy: y must be halved."}]}, {"id": "s10", "label": "Assessment C", "sub": "Communicating", "slides": [{"kind": "mcq", "text": "<b>Check-up · Journal</b> · How can you write 3 : 5 as a decimal and as a percentage? Would you be right in using the word ‘proportional’ to describe the conversions?", "opts": ["0.35 and 35%; no, a percentage is not a ratio at all", "0.6 and 6%; yes, both of them are written with a 6", "0.6 and 60%; yes, 3 : 5, 0.6 : 1 and 60 : 100 are equal ratios", "1.67 and 167%; no, a decimal cannot be part of a ratio"], "correct": 2, "tag": "", "sol": "3 ÷ 5 = 0.6 = {60/100} = 60%. 3 : 5, 0.6 : 1 and 60 : 100 are equal ratios, so they form proportions (3 × 100 = 5 × 60)."}, {"kind": "blank", "p": "<b>Check-up · Q16</b> · If 16 men can make 320 art pieces in one day, how many men will be needed to make 960 such art pieces in one day?", "tag": "", "marks": "", "flat": [{"t": "Men needed = __B1__", "a": {"B1": "48"}}, {"t": "This is a __B1__ proportion (direct / inverse).", "a": {"B1": "direct"}, "expr": "words", "accept": ["direct variation"]}], "sol": "960 is 3 times 320, so 3 × 16 = 48 men.\nMore art pieces need more men."}, {"kind": "blank", "p": "<b>Check-up · Q17</b> · Sony and Ranu together can do a piece of work in 20 days. Sony alone can finish the work in 30 days. If Ranu had been doing it alone, how long would she take?", "tag": "", "marks": "", "flat": [{"t": "Ranu’s one day’s work = __B1__", "a": {"B1": "1/60"}, "expr": "fl"}, {"t": "Ranu alone takes __B1__ days", "a": {"B1": "60"}}], "sol": "{1/20} − {1/30} = (3 − 2)/60 = {1/60}.\n1 ÷ {1/60} = 60 days."}, {"kind": "mcq", "text": "<b>Check-up · Q18</b> · On a library shelf, 150 books each of thickness 3 cm can be stacked. If books each of thickness 2 cm are to be stacked in the same shelf, how many such books can be stacked? Which reasoning is correct?", "opts": ["Inverse proportion: 150 ÷ 3 × 2 = 100 books", "Inverse proportion: 150 × 3 = 2 × x, so 225 books", "Inverse proportion: 150 × 2 = 300 books, twice as many", "Direct proportion: {150/3} = {x/2}, so 100 books"], "correct": 1, "tag": "", "sol": "The shelf length 450 cm is fixed; thinner books means more books. 450 ÷ 2 = 225 books."}, {"kind": "mcq", "text": "Riya says: “A train 200 m long crossing a 300 m platform covers 300 m.” What is wrong?", "opts": ["Nothing; only the platform length counts", "It covers 200 m, its own length", "It covers 300 − 200 = 100 m", "The train covers its own length too: 200 + 300 = 500 m"], "correct": 3, "tag": "", "sol": "The engine must travel the whole platform and then the rest of the train must leave it: 200 + 300 = 500 m."}, {"kind": "blank", "p": "Explain the method for “x varies inversely as y; x = 8 when y = 5; find y when x = 10”.", "tag": "", "marks": "", "flat": [{"t": "The product xy = __B1__", "a": {"B1": "40"}}, {"t": "Since the __B1__ is constant, divide it by the new x.", "a": {"B1": "product"}, "expr": "words", "accept": ["product xy"]}, {"t": "y = __B1__", "a": {"B1": "4"}}], "sol": "8 × 5 = 40.\nIn inverse variation the product stays the same.\n40 ÷ 10 = 4."}, {"kind": "mcq", "text": "Aman says “x : y = 2 : 3 and 4 : 5 is also true, so x, y are in direct proportion.” Which reply is correct?", "opts": ["Yes, both ratios are less than 1", "No, 2 : 3 and 4 : 5 are not equal ratios ({10/15} ≠ {12/15}), so the ratio x : y is not constant", "No, because direct proportion needs x × y constant", "Yes, both numbers went up by 2"], "correct": 1, "tag": "", "sol": "Direct proportion needs the same ratio every time. 2 × 5 = 10 but 3 × 4 = 12, so 2 : 3 ≠ 4 : 5."}]}, {"id": "s11", "label": "Assessment D", "sub": "Applying mathematics in real-life contexts", "slides": [{"kind": "mcq", "text": "<b>Check-up · Q7</b> · A recipe needs one cup of flour and {1 1/2} cups of sugar. If 3 cups of flour are used, how much sugar is needed?", "opts": ["{4 1/2} cups", "3 cups", "{1/2} cup", "{3 1/2} cups"], "correct": 0, "tag": "", "sol": "Flour and sugar vary directly: 3 cups of flour is 3 times as much, so sugar = 3 × {3/2} = {9/2} = {4 1/2} cups. (Adding 2 cups to the sugar gives the wrong answer {3 1/2}.)"}, {"kind": "blank", "p": "<b>Check-up · Q14</b> · If {1/4} kg of a sweet costs ₹52, find the cost of {2 1/2} kg of the same sweet.", "tag": "", "marks": "", "flat": [{"t": "Cost of 1 kg = ₹__B1__", "a": {"B1": "208"}}, {"t": "Cost of {2 1/2} kg = ₹__B1__", "a": {"B1": "520"}}], "sol": "52 × 4 = ₹208.\n208 × {5/2} = ₹520."}, {"kind": "blank", "p": "<b>Check-up · Q19</b> · Case study: a 400 m long train starts from city A at 5:00 a.m. and reaches city B at 6:00 a.m., covering a distance of 150 km.", "tag": "", "marks": "", "flat": [{"t": "a) Time to cross an 800 m long bridge = __B1__ s", "a": {"B1": "144/5"}, "expr": "fv"}, {"t": "b) At 120 km/h the train passes a bridge in 21 s. Length of the bridge = __B1__ m", "a": {"B1": "300"}}, {"t": "c) Time for another train, speed 72 km/h and half the length of this train, to pass this train standing at a platform = __B1__ s", "a": {"B1": "30"}}], "sol": "Speed = 150 km/h = 150 × {5/18} = {125/3} m/s. Distance = 400 + 800 = 1200 m; 1200 ÷ {125/3} = 28.8 s.\n120 km/h = {100/3} m/s; in 21 s it covers 700 m = 400 m train + bridge, so the bridge is 300 m.\n72 km/h = 20 m/s; distance = 200 m + 400 m = 600 m; 600 ÷ 20 = 30 s."}, {"kind": "mcq", "text": "<b>Check-up · Q20</b> · A school buys 40 blackboards at ₹650 each. If each blackboard were to cost ₹150 less, how many blackboards in total could have been bought with the same money?", "opts": ["54", "46", "30", "52"], "correct": 3, "tag": "", "sol": "Money = 40 × 650 = ₹26,000. New price ₹500; 26000 ÷ 500 = 52 blackboards."}, {"kind": "blank", "p": "<b>Check-up · Q21</b> · Working for 8 hours daily, 40 people can dig the foundation of a building in 21 days. Working for 10 hours daily, if the work is to be finished in 14 days, how many people are needed?", "tag": "", "marks": "", "flat": [{"t": "Total person-hours = __B1__", "a": {"B1": "6720"}}, {"t": "People needed = __B1__", "a": {"B1": "48"}}], "sol": "40 × 8 × 21 = 6720 person-hours.\nEach person gives 10 × 14 = 140 hours; 6720 ÷ 140 = 48 people."}, {"kind": "blank", "p": "<b>Check-up · Q22</b> · Roshan alone can build a fence in 20 days. He starts the work and leaves it after 5 days. Ramesh does the remaining work in 12 days.", "tag": "", "marks": "", "flat": [{"t": "Work left for Ramesh = __B1__", "a": {"B1": "3/4"}, "expr": "fl"}, {"t": "Ramesh alone would take __B1__ days", "a": {"B1": "16"}}, {"t": "Roshan and Ramesh together from the beginning take __B1__ days", "a": {"B1": "80/9"}, "expr": "fl"}], "sol": "Roshan does {5/20} = {1/4}; {3/4} is left.\n{3/4} in 12 days, so the whole in 12 ÷ {3/4} = 16 days.\n{1/20} + {1/16} = (4 + 5)/80 = {9/80} per day; time = {80/9} = {8 8/9} days."}, {"kind": "mcq", "text": "<b>CT Worksheet · Q1</b> · The double bar graph shows the percentage of people who invested in the stock market in 1990 and 2023 in cities A–E. True or false: “If the number of people who invested in the stock market in city B was 20,000 in 1990 and 2,70,000 in 2023, then the ratio of the population of city B in 1990 to that in 2023 is 1 : 6.”", "opts": ["True: the populations were 1,00,000 and 6,00,000, and 1,00,000 : 6,00,000 = 1 : 6", "False: the populations were 4,00,000 and 6,00,000, so the ratio is 2 : 3", "False: 20,000 : 2,70,000 = 2 : 27, so the ratio is 2 : 27", "False: 20% : 45% = 4 : 9, so the ratio is 4 : 9"], "correct": 0, "tag": "", "sol": "City B: 20% invested in 1990 and 45% in 2023. Population in 1990 = 20,000 ÷ {20/100} = 1,00,000. Population in 2023 = 2,70,000 ÷ {45/100} = 6,00,000. Ratio 1,00,000 : 6,00,000 = 1 : 6, so the statement is true.", "fig": "<svg class=\"figsvg\" viewBox=\"0 0 330 250\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><text x=\"165.0\" y=\"11.0\" text-anchor=\"middle\" dominant-baseline=\"middle\" style=\"fill:var(--ink);font:700 11px 'Source Sans 3',sans-serif\">People investing in the stock market (%)</text><line x1=\"38\" y1=\"216.0\" x2=\"322\" y2=\"216.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><text x=\"34.0\" y=\"216.0\" text-anchor=\"end\" dominant-baseline=\"middle\" style=\"fill:var(--ink);font:600 9px 'Source Sans 3',sans-serif\">0%</text><line x1=\"38\" y1=\"199.6\" x2=\"322\" y2=\"199.6\" style=\"stroke:var(--rule);stroke-width:.8\"/><text x=\"34.0\" y=\"199.6\" text-anchor=\"end\" dominant-baseline=\"middle\" style=\"fill:var(--ink);font:600 9px 'Source Sans 3',sans-serif\">5%</text><line x1=\"38\" y1=\"183.2\" x2=\"322\" y2=\"183.2\" style=\"stroke:var(--rule);stroke-width:.8\"/><text x=\"34.0\" y=\"183.2\" text-anchor=\"end\" dominant-baseline=\"middle\" style=\"fill:var(--ink);font:600 9px 'Source Sans 3',sans-serif\">10%</text><line x1=\"38\" y1=\"166.8\" x2=\"322\" y2=\"166.8\" style=\"stroke:var(--rule);stroke-width:.8\"/><text x=\"34.0\" y=\"166.8\" text-anchor=\"end\" dominant-baseline=\"middle\" style=\"fill:var(--ink);font:600 9px 'Source Sans 3',sans-serif\">15%</text><line x1=\"38\" y1=\"150.4\" x2=\"322\" y2=\"150.4\" style=\"stroke:var(--rule);stroke-width:.8\"/><text x=\"34.0\" y=\"150.4\" text-anchor=\"end\" dominant-baseline=\"middle\" style=\"fill:var(--ink);font:600 9px 'Source Sans 3',sans-serif\">20%</text><line x1=\"38\" y1=\"134.0\" x2=\"322\" y2=\"134.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><text x=\"34.0\" y=\"134.0\" text-anchor=\"end\" dominant-baseline=\"middle\" style=\"fill:var(--ink);font:600 9px 'Source Sans 3',sans-serif\">25%</text><line x1=\"38\" y1=\"117.6\" x2=\"322\" y2=\"117.6\" style=\"stroke:var(--rule);stroke-width:.8\"/><text x=\"34.0\" y=\"117.6\" text-anchor=\"end\" dominant-baseline=\"middle\" style=\"fill:var(--ink);font:600 9px 'Source Sans 3',sans-serif\">30%</text><line x1=\"38\" y1=\"101.2\" x2=\"322\" y2=\"101.2\" style=\"stroke:var(--rule);stroke-width:.8\"/><text x=\"34.0\" y=\"101.2\" text-anchor=\"end\" dominant-baseline=\"middle\" style=\"fill:var(--ink);font:600 9px 'Source Sans 3',sans-serif\">35%</text><line x1=\"38\" y1=\"84.8\" x2=\"322\" y2=\"84.8\" style=\"stroke:var(--rule);stroke-width:.8\"/><text x=\"34.0\" y=\"84.8\" text-anchor=\"end\" dominant-baseline=\"middle\" style=\"fill:var(--ink);font:600 9px 'Source Sans 3',sans-serif\">40%</text><line x1=\"38\" y1=\"68.4\" x2=\"322\" y2=\"68.4\" style=\"stroke:var(--rule);stroke-width:.8\"/><text x=\"34.0\" y=\"68.4\" text-anchor=\"end\" dominant-baseline=\"middle\" style=\"fill:var(--ink);font:600 9px 'Source Sans 3',sans-serif\">45%</text><line x1=\"38\" y1=\"52.0\" x2=\"322\" y2=\"52.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><text x=\"34.0\" y=\"52.0\" text-anchor=\"end\" dominant-baseline=\"middle\" style=\"fill:var(--ink);font:600 9px 'Source Sans 3',sans-serif\">50%</text><rect x=\"47.1\" y=\"199.6\" width=\"19.3\" height=\"16.4\" style=\"fill:var(--accent-text);fill-opacity:.55;stroke:var(--accent-text);stroke-width:1.1\"/><rect x=\"66.4\" y=\"166.8\" width=\"19.3\" height=\"49.2\" style=\"fill:var(--danger);fill-opacity:.55;stroke:var(--danger);stroke-width:1.1\"/><text x=\"66.4\" y=\"227.0\" text-anchor=\"middle\" dominant-baseline=\"middle\" style=\"fill:var(--ink);font:600 10px 'Source Sans 3',sans-serif\">A</text><rect x=\"103.9\" y=\"150.4\" width=\"19.3\" height=\"65.6\" style=\"fill:var(--accent-text);fill-opacity:.55;stroke:var(--accent-text);stroke-width:1.1\"/><rect x=\"123.2\" y=\"68.4\" width=\"19.3\" height=\"147.6\" style=\"fill:var(--danger);fill-opacity:.55;stroke:var(--danger);stroke-width:1.1\"/><text x=\"123.2\" y=\"227.0\" text-anchor=\"middle\" dominant-baseline=\"middle\" style=\"fill:var(--ink);font:600 10px 'Source Sans 3',sans-serif\">B</text><rect x=\"160.7\" y=\"166.8\" width=\"19.3\" height=\"49.2\" style=\"fill:var(--accent-text);fill-opacity:.55;stroke:var(--accent-text);stroke-width:1.1\"/><rect x=\"180.0\" y=\"183.2\" width=\"19.3\" height=\"32.8\" style=\"fill:var(--danger);fill-opacity:.55;stroke:var(--danger);stroke-width:1.1\"/><text x=\"180.0\" y=\"227.0\" text-anchor=\"middle\" dominant-baseline=\"middle\" style=\"fill:var(--ink);font:600 10px 'Source Sans 3',sans-serif\">C</text><rect x=\"217.5\" y=\"183.2\" width=\"19.3\" height=\"32.8\" style=\"fill:var(--accent-text);fill-opacity:.55;stroke:var(--accent-text);stroke-width:1.1\"/><rect x=\"236.8\" y=\"101.2\" width=\"19.3\" height=\"114.8\" style=\"fill:var(--danger);fill-opacity:.55;stroke:var(--danger);stroke-width:1.1\"/><text x=\"236.8\" y=\"227.0\" text-anchor=\"middle\" dominant-baseline=\"middle\" style=\"fill:var(--ink);font:600 10px 'Source Sans 3',sans-serif\">D</text><rect x=\"274.3\" y=\"183.2\" width=\"19.3\" height=\"32.8\" style=\"fill:var(--accent-text);fill-opacity:.55;stroke:var(--accent-text);stroke-width:1.1\"/><rect x=\"293.6\" y=\"150.4\" width=\"19.3\" height=\"65.6\" style=\"fill:var(--danger);fill-opacity:.55;stroke:var(--danger);stroke-width:1.1\"/><text x=\"293.6\" y=\"227.0\" text-anchor=\"middle\" dominant-baseline=\"middle\" style=\"fill:var(--ink);font:600 10px 'Source Sans 3',sans-serif\">E</text><text x=\"180.0\" y=\"242.0\" text-anchor=\"middle\" dominant-baseline=\"middle\" style=\"fill:var(--ink);font:600 10px 'Source Sans 3',sans-serif\">City</text><rect x=\"42\" y=\"22\" width=\"11\" height=\"11\" style=\"fill:var(--accent-text);fill-opacity:.55;stroke:var(--accent-text)\"/><text x=\"57.0\" y=\"28.0\" text-anchor=\"start\" dominant-baseline=\"middle\" style=\"fill:var(--ink);font:600 10px 'Source Sans 3',sans-serif\">1990</text><rect x=\"97\" y=\"22\" width=\"11\" height=\"11\" style=\"fill:var(--danger);fill-opacity:.55;stroke:var(--danger)\"/><text x=\"112.0\" y=\"28.0\" text-anchor=\"start\" dominant-baseline=\"middle\" style=\"fill:var(--ink);font:600 10px 'Source Sans 3',sans-serif\">2023</text><line x1=\"38\" y1=\"216.0\" x2=\"322\" y2=\"216.0\" style=\"stroke:var(--ink-soft);stroke-width:1.3\"/><line x1=\"38\" y1=\"216.0\" x2=\"38\" y2=\"52.0\" style=\"stroke:var(--ink-soft);stroke-width:1.3\"/></svg>"}, {"kind": "mcq", "text": "<b>CT Worksheet · Q2</b> · Use the same double bar graph. True or false: “From the year 1990 to 2023, the percentage of people investing in the stock market has increased in all the cities.”", "opts": ["True: the 2023 bar is the taller bar for every city", "True: the total rose from 60% to 125%", "False: in city E it stayed the same at 10%", "False: in city C it fell from 15% to 10%"], "correct": 3, "tag": "", "sol": "Compare the two bars for each city: A 5% → 15%, B 20% → 45%, C 15% → 10%, D 10% → 35%, E 10% → 20%. City C decreased, so the statement is false.", "fig": "<svg class=\"figsvg\" viewBox=\"0 0 330 250\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><text x=\"165.0\" y=\"11.0\" text-anchor=\"middle\" dominant-baseline=\"middle\" style=\"fill:var(--ink);font:700 11px 'Source Sans 3',sans-serif\">People investing in the stock market (%)</text><line x1=\"38\" y1=\"216.0\" x2=\"322\" y2=\"216.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><text x=\"34.0\" y=\"216.0\" text-anchor=\"end\" dominant-baseline=\"middle\" style=\"fill:var(--ink);font:600 9px 'Source Sans 3',sans-serif\">0%</text><line x1=\"38\" y1=\"199.6\" x2=\"322\" y2=\"199.6\" style=\"stroke:var(--rule);stroke-width:.8\"/><text x=\"34.0\" y=\"199.6\" text-anchor=\"end\" dominant-baseline=\"middle\" style=\"fill:var(--ink);font:600 9px 'Source Sans 3',sans-serif\">5%</text><line x1=\"38\" y1=\"183.2\" x2=\"322\" y2=\"183.2\" style=\"stroke:var(--rule);stroke-width:.8\"/><text x=\"34.0\" y=\"183.2\" text-anchor=\"end\" dominant-baseline=\"middle\" style=\"fill:var(--ink);font:600 9px 'Source Sans 3',sans-serif\">10%</text><line x1=\"38\" y1=\"166.8\" x2=\"322\" y2=\"166.8\" style=\"stroke:var(--rule);stroke-width:.8\"/><text x=\"34.0\" y=\"166.8\" text-anchor=\"end\" dominant-baseline=\"middle\" style=\"fill:var(--ink);font:600 9px 'Source Sans 3',sans-serif\">15%</text><line x1=\"38\" y1=\"150.4\" x2=\"322\" y2=\"150.4\" style=\"stroke:var(--rule);stroke-width:.8\"/><text x=\"34.0\" y=\"150.4\" text-anchor=\"end\" dominant-baseline=\"middle\" style=\"fill:var(--ink);font:600 9px 'Source Sans 3',sans-serif\">20%</text><line x1=\"38\" y1=\"134.0\" x2=\"322\" y2=\"134.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><text x=\"34.0\" y=\"134.0\" text-anchor=\"end\" dominant-baseline=\"middle\" style=\"fill:var(--ink);font:600 9px 'Source Sans 3',sans-serif\">25%</text><line x1=\"38\" y1=\"117.6\" x2=\"322\" y2=\"117.6\" style=\"stroke:var(--rule);stroke-width:.8\"/><text x=\"34.0\" y=\"117.6\" text-anchor=\"end\" dominant-baseline=\"middle\" style=\"fill:var(--ink);font:600 9px 'Source Sans 3',sans-serif\">30%</text><line x1=\"38\" y1=\"101.2\" x2=\"322\" y2=\"101.2\" style=\"stroke:var(--rule);stroke-width:.8\"/><text x=\"34.0\" y=\"101.2\" text-anchor=\"end\" dominant-baseline=\"middle\" style=\"fill:var(--ink);font:600 9px 'Source Sans 3',sans-serif\">35%</text><line x1=\"38\" y1=\"84.8\" x2=\"322\" y2=\"84.8\" style=\"stroke:var(--rule);stroke-width:.8\"/><text x=\"34.0\" y=\"84.8\" text-anchor=\"end\" dominant-baseline=\"middle\" style=\"fill:var(--ink);font:600 9px 'Source Sans 3',sans-serif\">40%</text><line x1=\"38\" y1=\"68.4\" x2=\"322\" y2=\"68.4\" style=\"stroke:var(--rule);stroke-width:.8\"/><text x=\"34.0\" y=\"68.4\" text-anchor=\"end\" dominant-baseline=\"middle\" style=\"fill:var(--ink);font:600 9px 'Source Sans 3',sans-serif\">45%</text><line x1=\"38\" y1=\"52.0\" x2=\"322\" y2=\"52.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><text x=\"34.0\" y=\"52.0\" text-anchor=\"end\" dominant-baseline=\"middle\" style=\"fill:var(--ink);font:600 9px 'Source Sans 3',sans-serif\">50%</text><rect x=\"47.1\" y=\"199.6\" width=\"19.3\" height=\"16.4\" style=\"fill:var(--accent-text);fill-opacity:.55;stroke:var(--accent-text);stroke-width:1.1\"/><rect x=\"66.4\" y=\"166.8\" width=\"19.3\" height=\"49.2\" style=\"fill:var(--danger);fill-opacity:.55;stroke:var(--danger);stroke-width:1.1\"/><text x=\"66.4\" y=\"227.0\" text-anchor=\"middle\" dominant-baseline=\"middle\" style=\"fill:var(--ink);font:600 10px 'Source Sans 3',sans-serif\">A</text><rect x=\"103.9\" y=\"150.4\" width=\"19.3\" height=\"65.6\" style=\"fill:var(--accent-text);fill-opacity:.55;stroke:var(--accent-text);stroke-width:1.1\"/><rect x=\"123.2\" y=\"68.4\" width=\"19.3\" height=\"147.6\" style=\"fill:var(--danger);fill-opacity:.55;stroke:var(--danger);stroke-width:1.1\"/><text x=\"123.2\" y=\"227.0\" text-anchor=\"middle\" dominant-baseline=\"middle\" style=\"fill:var(--ink);font:600 10px 'Source Sans 3',sans-serif\">B</text><rect x=\"160.7\" y=\"166.8\" width=\"19.3\" height=\"49.2\" style=\"fill:var(--accent-text);fill-opacity:.55;stroke:var(--accent-text);stroke-width:1.1\"/><rect x=\"180.0\" y=\"183.2\" width=\"19.3\" height=\"32.8\" style=\"fill:var(--danger);fill-opacity:.55;stroke:var(--danger);stroke-width:1.1\"/><text x=\"180.0\" y=\"227.0\" text-anchor=\"middle\" dominant-baseline=\"middle\" style=\"fill:var(--ink);font:600 10px 'Source Sans 3',sans-serif\">C</text><rect x=\"217.5\" y=\"183.2\" width=\"19.3\" height=\"32.8\" style=\"fill:var(--accent-text);fill-opacity:.55;stroke:var(--accent-text);stroke-width:1.1\"/><rect x=\"236.8\" y=\"101.2\" width=\"19.3\" height=\"114.8\" style=\"fill:var(--danger);fill-opacity:.55;stroke:var(--danger);stroke-width:1.1\"/><text x=\"236.8\" y=\"227.0\" text-anchor=\"middle\" dominant-baseline=\"middle\" style=\"fill:var(--ink);font:600 10px 'Source Sans 3',sans-serif\">D</text><rect x=\"274.3\" y=\"183.2\" width=\"19.3\" height=\"32.8\" style=\"fill:var(--accent-text);fill-opacity:.55;stroke:var(--accent-text);stroke-width:1.1\"/><rect x=\"293.6\" y=\"150.4\" width=\"19.3\" height=\"65.6\" style=\"fill:var(--danger);fill-opacity:.55;stroke:var(--danger);stroke-width:1.1\"/><text x=\"293.6\" y=\"227.0\" text-anchor=\"middle\" dominant-baseline=\"middle\" style=\"fill:var(--ink);font:600 10px 'Source Sans 3',sans-serif\">E</text><text x=\"180.0\" y=\"242.0\" text-anchor=\"middle\" dominant-baseline=\"middle\" style=\"fill:var(--ink);font:600 10px 'Source Sans 3',sans-serif\">City</text><rect x=\"42\" y=\"22\" width=\"11\" height=\"11\" style=\"fill:var(--accent-text);fill-opacity:.55;stroke:var(--accent-text)\"/><text x=\"57.0\" y=\"28.0\" text-anchor=\"start\" dominant-baseline=\"middle\" style=\"fill:var(--ink);font:600 10px 'Source Sans 3',sans-serif\">1990</text><rect x=\"97\" y=\"22\" width=\"11\" height=\"11\" style=\"fill:var(--danger);fill-opacity:.55;stroke:var(--danger)\"/><text x=\"112.0\" y=\"28.0\" text-anchor=\"start\" dominant-baseline=\"middle\" style=\"fill:var(--ink);font:600 10px 'Source Sans 3',sans-serif\">2023</text><line x1=\"38\" y1=\"216.0\" x2=\"322\" y2=\"216.0\" style=\"stroke:var(--ink-soft);stroke-width:1.3\"/><line x1=\"38\" y1=\"216.0\" x2=\"38\" y2=\"52.0\" style=\"stroke:var(--ink-soft);stroke-width:1.3\"/></svg>"}, {"kind": "blank", "p": "<b>CT Worksheet · Q3</b> · Use the same double bar graph. The population of city E was 2,00,000 in 1990 and 7,00,000 in 2023. Test the statement: “the number of people who invested in the stock market was 14,000 in 1990 and 2000 in 2023.”", "tag": "", "marks": "", "flat": [{"t": "People in E who invested in 1990 = 10% of 2,00,000 = __B1__", "a": {"B1": "20000"}}, {"t": "People in E who invested in 2023 = 20% of 7,00,000 = __B1__", "a": {"B1": "140000"}}, {"t": "So the statement is __B1__ (true / false).", "a": {"B1": "false"}, "expr": "words"}], "sol": "City E’s 1990 bar is at 10%: {10/100} × 2,00,000 = 20,000.\nCity E’s 2023 bar is at 20%: {20/100} × 7,00,000 = 1,40,000.\nThe statement says 14,000 and 2000, which do not match 20,000 and 1,40,000, so it is false.", "fig": "<svg class=\"figsvg\" viewBox=\"0 0 330 250\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><text x=\"165.0\" y=\"11.0\" text-anchor=\"middle\" dominant-baseline=\"middle\" style=\"fill:var(--ink);font:700 11px 'Source Sans 3',sans-serif\">People investing in the stock market (%)</text><line x1=\"38\" y1=\"216.0\" x2=\"322\" y2=\"216.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><text x=\"34.0\" y=\"216.0\" text-anchor=\"end\" dominant-baseline=\"middle\" style=\"fill:var(--ink);font:600 9px 'Source Sans 3',sans-serif\">0%</text><line x1=\"38\" y1=\"199.6\" x2=\"322\" y2=\"199.6\" style=\"stroke:var(--rule);stroke-width:.8\"/><text x=\"34.0\" y=\"199.6\" text-anchor=\"end\" dominant-baseline=\"middle\" style=\"fill:var(--ink);font:600 9px 'Source Sans 3',sans-serif\">5%</text><line x1=\"38\" y1=\"183.2\" x2=\"322\" y2=\"183.2\" style=\"stroke:var(--rule);stroke-width:.8\"/><text x=\"34.0\" y=\"183.2\" text-anchor=\"end\" dominant-baseline=\"middle\" style=\"fill:var(--ink);font:600 9px 'Source Sans 3',sans-serif\">10%</text><line x1=\"38\" y1=\"166.8\" x2=\"322\" y2=\"166.8\" style=\"stroke:var(--rule);stroke-width:.8\"/><text x=\"34.0\" y=\"166.8\" text-anchor=\"end\" dominant-baseline=\"middle\" style=\"fill:var(--ink);font:600 9px 'Source Sans 3',sans-serif\">15%</text><line x1=\"38\" y1=\"150.4\" x2=\"322\" y2=\"150.4\" style=\"stroke:var(--rule);stroke-width:.8\"/><text x=\"34.0\" y=\"150.4\" text-anchor=\"end\" dominant-baseline=\"middle\" style=\"fill:var(--ink);font:600 9px 'Source Sans 3',sans-serif\">20%</text><line x1=\"38\" y1=\"134.0\" x2=\"322\" y2=\"134.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><text x=\"34.0\" y=\"134.0\" text-anchor=\"end\" dominant-baseline=\"middle\" style=\"fill:var(--ink);font:600 9px 'Source Sans 3',sans-serif\">25%</text><line x1=\"38\" y1=\"117.6\" x2=\"322\" y2=\"117.6\" style=\"stroke:var(--rule);stroke-width:.8\"/><text x=\"34.0\" y=\"117.6\" text-anchor=\"end\" dominant-baseline=\"middle\" style=\"fill:var(--ink);font:600 9px 'Source Sans 3',sans-serif\">30%</text><line x1=\"38\" y1=\"101.2\" x2=\"322\" y2=\"101.2\" style=\"stroke:var(--rule);stroke-width:.8\"/><text x=\"34.0\" y=\"101.2\" text-anchor=\"end\" dominant-baseline=\"middle\" style=\"fill:var(--ink);font:600 9px 'Source Sans 3',sans-serif\">35%</text><line x1=\"38\" y1=\"84.8\" x2=\"322\" y2=\"84.8\" style=\"stroke:var(--rule);stroke-width:.8\"/><text x=\"34.0\" y=\"84.8\" text-anchor=\"end\" dominant-baseline=\"middle\" style=\"fill:var(--ink);font:600 9px 'Source Sans 3',sans-serif\">40%</text><line x1=\"38\" y1=\"68.4\" x2=\"322\" y2=\"68.4\" style=\"stroke:var(--rule);stroke-width:.8\"/><text x=\"34.0\" y=\"68.4\" text-anchor=\"end\" dominant-baseline=\"middle\" style=\"fill:var(--ink);font:600 9px 'Source Sans 3',sans-serif\">45%</text><line x1=\"38\" y1=\"52.0\" x2=\"322\" y2=\"52.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><text x=\"34.0\" y=\"52.0\" text-anchor=\"end\" dominant-baseline=\"middle\" style=\"fill:var(--ink);font:600 9px 'Source Sans 3',sans-serif\">50%</text><rect x=\"47.1\" y=\"199.6\" width=\"19.3\" height=\"16.4\" style=\"fill:var(--accent-text);fill-opacity:.55;stroke:var(--accent-text);stroke-width:1.1\"/><rect x=\"66.4\" y=\"166.8\" width=\"19.3\" height=\"49.2\" style=\"fill:var(--danger);fill-opacity:.55;stroke:var(--danger);stroke-width:1.1\"/><text x=\"66.4\" y=\"227.0\" text-anchor=\"middle\" dominant-baseline=\"middle\" style=\"fill:var(--ink);font:600 10px 'Source Sans 3',sans-serif\">A</text><rect x=\"103.9\" y=\"150.4\" width=\"19.3\" height=\"65.6\" style=\"fill:var(--accent-text);fill-opacity:.55;stroke:var(--accent-text);stroke-width:1.1\"/><rect x=\"123.2\" y=\"68.4\" width=\"19.3\" height=\"147.6\" style=\"fill:var(--danger);fill-opacity:.55;stroke:var(--danger);stroke-width:1.1\"/><text x=\"123.2\" y=\"227.0\" text-anchor=\"middle\" dominant-baseline=\"middle\" style=\"fill:var(--ink);font:600 10px 'Source Sans 3',sans-serif\">B</text><rect x=\"160.7\" y=\"166.8\" width=\"19.3\" height=\"49.2\" style=\"fill:var(--accent-text);fill-opacity:.55;stroke:var(--accent-text);stroke-width:1.1\"/><rect x=\"180.0\" y=\"183.2\" width=\"19.3\" height=\"32.8\" style=\"fill:var(--danger);fill-opacity:.55;stroke:var(--danger);stroke-width:1.1\"/><text x=\"180.0\" y=\"227.0\" text-anchor=\"middle\" dominant-baseline=\"middle\" style=\"fill:var(--ink);font:600 10px 'Source Sans 3',sans-serif\">C</text><rect x=\"217.5\" y=\"183.2\" width=\"19.3\" height=\"32.8\" style=\"fill:var(--accent-text);fill-opacity:.55;stroke:var(--accent-text);stroke-width:1.1\"/><rect x=\"236.8\" y=\"101.2\" width=\"19.3\" height=\"114.8\" style=\"fill:var(--danger);fill-opacity:.55;stroke:var(--danger);stroke-width:1.1\"/><text x=\"236.8\" y=\"227.0\" text-anchor=\"middle\" dominant-baseline=\"middle\" style=\"fill:var(--ink);font:600 10px 'Source Sans 3',sans-serif\">D</text><rect x=\"274.3\" y=\"183.2\" width=\"19.3\" height=\"32.8\" style=\"fill:var(--accent-text);fill-opacity:.55;stroke:var(--accent-text);stroke-width:1.1\"/><rect x=\"293.6\" y=\"150.4\" width=\"19.3\" height=\"65.6\" style=\"fill:var(--danger);fill-opacity:.55;stroke:var(--danger);stroke-width:1.1\"/><text x=\"293.6\" y=\"227.0\" text-anchor=\"middle\" dominant-baseline=\"middle\" style=\"fill:var(--ink);font:600 10px 'Source Sans 3',sans-serif\">E</text><text x=\"180.0\" y=\"242.0\" text-anchor=\"middle\" dominant-baseline=\"middle\" style=\"fill:var(--ink);font:600 10px 'Source Sans 3',sans-serif\">City</text><rect x=\"42\" y=\"22\" width=\"11\" height=\"11\" style=\"fill:var(--accent-text);fill-opacity:.55;stroke:var(--accent-text)\"/><text x=\"57.0\" y=\"28.0\" text-anchor=\"start\" dominant-baseline=\"middle\" style=\"fill:var(--ink);font:600 10px 'Source Sans 3',sans-serif\">1990</text><rect x=\"97\" y=\"22\" width=\"11\" height=\"11\" style=\"fill:var(--danger);fill-opacity:.55;stroke:var(--danger)\"/><text x=\"112.0\" y=\"28.0\" text-anchor=\"start\" dominant-baseline=\"middle\" style=\"fill:var(--ink);font:600 10px 'Source Sans 3',sans-serif\">2023</text><line x1=\"38\" y1=\"216.0\" x2=\"322\" y2=\"216.0\" style=\"stroke:var(--ink-soft);stroke-width:1.3\"/><line x1=\"38\" y1=\"216.0\" x2=\"38\" y2=\"52.0\" style=\"stroke:var(--ink-soft);stroke-width:1.3\"/></svg>"}, {"kind": "blank", "p": "<b>CT Worksheet · Algorithm</b> · In a spreadsheet, enter the Principal in cell A2, the Rate <b>as a decimal</b> in B2 (e.g. 5% → 0.05) and the Time in years in C2. The formula =A2*B2*C2 in cell D2 then shows the simple interest (P × R × T). Use this algorithm.", "tag": "", "marks": "", "flat": [{"t": "1(a) P = ₹1,00,00,000, R = 7%, T = 2 years: D2 shows ₹__B1__", "a": {"B1": "1400000"}}, {"t": "1(b) P = ₹2,00,000, R = 10%, T = 3 years: D2 shows ₹__B1__", "a": {"B1": "60000"}}, {"t": "2. Amount = Principal + Simple interest, so the formula in cell E2 is =A2 + __B1__", "a": {"B1": "D2"}, "accept": ["A2*B2*C2", "A2×B2×C2", "A2xB2xC2"]}, {"t": "With the values of 1(b), cell E2 shows ₹__B1__", "a": {"B1": "260000"}}], "sol": "B2 = 0.07: 1,00,00,000 × 0.07 × 2 = ₹14,00,000.\nB2 = 0.1: 2,00,000 × 0.1 × 3 = ₹60,000.\nThe simple interest is already in D2, so E2 = A2 + D2 (or =A2 + A2*B2*C2).\n2,00,000 + 60,000 = ₹2,60,000."}]}];
/* ================= build slide lists ================= */
var SLIDES = {}; SECTIONS.forEach(function(sec){ SLIDES[sec.id]=sec.slides; });
var TAB_DEFS = SECTIONS.map(function(sec){ return {id:sec.id, label:sec.label, sub:sec.sub}; });

/* ================= state ================= */
function blankItem(slide){
  if(slide.kind==='mcq'||slide.kind==='ar'){
    return {status:'unanswered', attempts:0, choice:undefined};
  }
  return {status:'unanswered', curStep:0, stepStates: slide.flat.map(function(){ return {status:'unanswered', attempts:0, inputs:{}}; })};
}
function defaultState(){
  var s={tabs:{}};
  TAB_DEFS.forEach(function(td){
    s.tabs[td.id] = { idx:0, maxReached:0, items: SLIDES[td.id].map(function(sl){ return blankItem(sl); }) };
  });
  return s;
}
var appState = {mode:null, learning:null, quiz:null};
var state = null;      // alias for appState[appState.mode]
var MODE = null;
var activeTab=TAB_DEFS[0].id;

function setMode(m){
  appState.mode = m;
  if(!appState[m]) appState[m] = defaultState();
  state = appState[m];
  MODE = m;
}
/* ================= student accounts (saved on this device) ================= */
var SHEET_KEY='sopaan-c8-ch12';
var ACC_KEY='sopaan-students-v1';
var storageOK=true;
var MEM={};
function lsGet(k){ var r=null; try{ r=localStorage.getItem(k); }catch(e){ storageOK=false; }
  if(r===null||r===undefined) r=MEM[k]||null; try{ return r?JSON.parse(r):null; }catch(e){ return null; } }
function lsSet(k,v){ var j=JSON.stringify(v); MEM[k]=j; try{ localStorage.setItem(k,j); return true; }catch(e){ storageOK=false; return false; } }
try{ localStorage.setItem('sopaan-probe','1'); localStorage.removeItem('sopaan-probe'); }catch(e){ storageOK=false; }
function hashPin(pin,salt){ var h=2166136261, str=salt+'|'+pin; for(var i=0;i<str.length;i++){ h^=str.charCodeAt(i); h=Math.imul(h,16777619)>>>0; } return h.toString(36); }
function accKey(name,roll){ return (name.trim().toLowerCase().replace(/\s+/g,' ')+'#'+roll.trim().toLowerCase()); }
function accounts(){ return lsGet(ACC_KEY)||{students:{}}; }
var student=null; // {key,name,roll}
var records=[];   // finished-tab history for this student on this sheet
function progKey(){ return SHEET_KEY+'::'+student.key; }

function loadState(){
  appState = {mode:null, learning:null, quiz:null}; records=[]; activeTab=TAB_DEFS[0].id;
  var saved=lsGet(progKey());
  if(!saved) return;
  try{
    ['learning','quiz'].forEach(function(m){
      if(saved[m] && saved[m].tabs){
        var fresh = defaultState();
        TAB_DEFS.forEach(function(td){
          if(saved[m].tabs[td.id] && saved[m].tabs[td.id].items && saved[m].tabs[td.id].items.length===SLIDES[td.id].length){
            fresh.tabs[td.id] = saved[m].tabs[td.id];
          }
        });
        appState[m] = fresh;
      }
    });
    if(saved.mode==='learning' || saved.mode==='quiz') appState.mode = saved.mode;
    if(saved.activeTab && TAB_DEFS.some(function(t){ return t.id===saved.activeTab; })) activeTab = saved.activeTab;
    if(Array.isArray(saved.records)) records = saved.records;
  }catch(e){}
}
function saveState(){
  if(!student) return;
  lsSet(progKey(), {mode:appState.mode, learning:appState.learning, quiz:appState.quiz, activeTab:activeTab, records:records, updated:Date.now()});
  var acc=accounts(); if(acc.students[student.key]){ acc.students[student.key].last=Date.now(); lsSet(ACC_KEY,acc); }
}
function addRecord(mode, tabId, correct, revealed, skipped, total){
  records.unshift({at:Date.now(), mode:mode, tab:tabId, correct:correct, revealed:revealed, skipped:skipped, total:total});
  if(records.length>60) records.length=60;
  saveState();
}
function fmtDate(ms){ try{ return new Date(ms).toLocaleString(undefined,{day:'numeric',month:'short',hour:'2-digit',minute:'2-digit'}); }catch(e){ return ''; } }

function renderWho(){
  var el=document.getElementById('whoBar');
  if(!student){ el.hidden=true; el.innerHTML=''; return; }
  el.hidden=false;
  el.innerHTML='Signed in as <b>'+esc(student.name)+'</b> · Roll '+esc(student.roll)+
    ' <button id="btnRecord">My record</button> <button id="btnSignOut">Sign out</button>';
  document.getElementById('btnRecord').addEventListener('click', renderRecord);
  document.getElementById('btnSignOut').addEventListener('click', signOut);
}
function signOut(){
  saveState(); student=null; state=null; MODE=null;
  var acc=accounts(); delete acc.current; lsSet(ACC_KEY,acc);
  document.getElementById('modePill').hidden=true;
  renderWho(); renderLogin();
}
function signIn(key){
  var acc=accounts(); var st=acc.students[key]; if(!st) return;
  student={key:key, name:st.name, roll:st.roll};
  acc.current=key; st.last=Date.now(); lsSet(ACC_KEY,acc);
  loadState(); renderWho();
  if(appState.mode==='learning' || appState.mode==='quiz'){
    setMode(appState.mode); document.getElementById('modePill').hidden=false; updateModePill();
    showChrome(true); buildTabbar(); renderSlide();
    showToast('Welcome back, '+st.name.split(' ')[0]+'. Picking up where you left off.');
  } else {
    renderModePicker();
  }
}
function renderLogin(msg){
  showChrome(false);
  var acc=accounts(); var keys=Object.keys(acc.students).sort(function(a,b){ return (acc.students[b].last||0)-(acc.students[a].last||0); });
  var h='<div class="login-card"><h2>Student sign-in</h2>'+
    '<p class="lead">Sign in to save your answers, see your record and continue where you left off next time.</p>';
  if(!storageOK) h+='<div class="login-err">This browser is blocking saved data (for example, a private window). You can still practise, but progress will not be kept after you close the page.</div>';
  if(msg) h+='<div class="login-err">'+esc(msg)+'</div>';
  if(keys.length){
    h+='<div class="known"><span class="known-label">Continue as</span>';
    keys.slice(0,6).forEach(function(k){ var st=acc.students[k];
      h+='<button class="known-btn" data-k="'+esc(k)+'"><span>'+esc(st.name)+' <small>· Roll '+esc(st.roll)+'</small></span><small>'+(st.last?'Last active '+fmtDate(st.last):'')+'</small></button>'; });
    h+='</div>';
  }
  h+='<form id="loginForm" novalidate>'+
    '<div class="fld"><label for="lgName">Full name</label><input id="lgName" autocomplete="name" required></div>'+
    '<div class="fld-row"><div class="fld"><label for="lgRoll">Roll no.</label><input id="lgRoll" required></div>'+
    '<div class="fld"><label for="lgPin">4-digit PIN</label><input id="lgPin" type="password" inputmode="numeric" maxlength="4" autocomplete="off" required></div></div>'+
    '<button class="btn btn-primary" type="submit" style="width:100%;">Sign in</button>'+
    '<p class="login-note">New here? Enter your name, roll no. and a PIN you will remember, and your profile is created. Progress is saved on this device, so use the same device and browser to continue.</p>'+
    '</form></div>';
  var wrap=document.getElementById('wrap'); wrap.innerHTML=h;
  wrap.querySelectorAll('.known-btn').forEach(function(b){
    b.addEventListener('click', function(){
      var st=accounts().students[b.dataset.k];
      document.getElementById('lgName').value=st.name; document.getElementById('lgRoll').value=st.roll;
      document.getElementById('lgPin').focus();
    });
  });
  document.getElementById('loginForm').addEventListener('submit', function(e){
    e.preventDefault();
    var name=document.getElementById('lgName').value.trim(), roll=document.getElementById('lgRoll').value.trim(), pin=document.getElementById('lgPin').value.trim();
    if(!name||!roll){ renderLoginErr('Enter your name and roll no.'); return; }
    if(!/^\d{4}$/.test(pin)){ renderLoginErr('Your PIN must be exactly 4 digits.'); return; }
    var k=accKey(name,roll); var acc=accounts();
    if(acc.students[k]){
      if(acc.students[k].pin!==hashPin(pin,k)){ renderLoginErr('That PIN does not match this name and roll no. Try again.'); return; }
    } else {
      acc.students[k]={name:name.replace(/\s+/g,' '), roll:roll, pin:hashPin(pin,k), created:Date.now()};
      lsSet(ACC_KEY,acc);
    }
    signIn(k);
  });
}
function renderLoginErr(m){
  var n=document.getElementById('lgName').value, r=document.getElementById('lgRoll').value;
  renderLogin(m); document.getElementById('lgName').value=n; document.getElementById('lgRoll').value=r; document.getElementById('lgPin').focus();
}
function tabSummary(m){
  var st=appState[m]; if(!st) return null;
  return TAB_DEFS.map(function(td){
    var items=st.tabs[td.id].items, n=items.length;
    var c=items.filter(function(i){return i.status==='correct';}).length;
    var done=items.filter(function(i){return i.status!=='unanswered';}).length;
    return {label:td.label, n:n, done:done, correct:c};
  });
}
function renderRecord(){
  showChrome(false);
  var tabLabel=function(id){ var t=TAB_DEFS.find(function(x){return x.id===id;}); return t?t.label:id; };
  var h='<div class="rec-card"><h2>'+esc(student.name)+'’s record</h2><p class="rec-empty" style="margin:0 0 12px;">Roll '+esc(student.roll)+' · Direct and Inverse Variations</p>';
  ['learning','quiz'].forEach(function(m){
    var sum=tabSummary(m);
    h+='<h3>'+(m==='learning'?'📘 Learning Sheet':'📝 Quiz Mode')+'</h3>';
    if(!sum){ h+='<p class="rec-empty">Not started yet.</p>'; return; }
    h+='<div class="rec-table-wrap"><table class="rec-table"><thead><tr><th>Section</th><th>Progress</th><th>Correct first time</th></tr></thead><tbody>';
    sum.forEach(function(r){ var pct=Math.round(r.done/r.n*100);
      h+='<tr><td>'+r.label+'</td><td><span class="rec-bar"><i style="width:'+pct+'%"></i></span>'+r.done+' / '+r.n+'</td><td>'+(m==='quiz'?'—':r.correct+' / '+r.n)+'</td></tr>'; });
    h+='</tbody></table></div>';
  });
  h+='</div><div class="rec-card"><h3>Finished sections</h3>';
  if(!records.length){ h+='<p class="rec-empty">No sections finished yet. Each time you finish a tab, your score is recorded here.</p>'; }
  else {
    h+='<div class="rec-table-wrap"><table class="rec-table"><thead><tr><th>When</th><th>Mode</th><th>Section</th><th>Score</th></tr></thead><tbody>';
    records.forEach(function(r){ h+='<tr><td>'+fmtDate(r.at)+'</td><td>'+(r.mode==='quiz'?'Quiz':'Learning')+'</td><td>'+tabLabel(r.tab)+'</td><td>'+r.correct+' / '+r.total+(r.mode==='learning'?' <span class="rec-empty">('+r.revealed+' revealed, '+r.skipped+' skipped)</span>':'')+'</td></tr>'; });
    h+='</tbody></table></div>';
  }
  h+='</div><button class="btn btn-primary" id="btnBack">'+(MODE?'Back to practice':'Choose a mode')+'</button>';
  document.getElementById('wrap').innerHTML=h;
  document.getElementById('btnBack').addEventListener('click', function(){
    if(MODE){ showChrome(true); buildTabbar(); renderSlide(); } else renderModePicker();
  });
  window.scrollTo({top:0});
}

/* ================= tab bar ================= */
function buildTabbar(){
  var el=document.getElementById('tabbar');
  el.innerHTML = '<button class="tab-btn'+(activeTab==='theory'?' active':'')+'" data-tab="theory">Theory<span class="tab-count">notes</span></button>' + TAB_DEFS.map(function(t){
    return '<button class="tab-btn'+(t.id===activeTab?' active':'')+'" data-tab="'+t.id+'">'+t.label+'<span class="tab-count">'+SLIDES[t.id].length+'</span></button>';
  }).join('') + '<button class="tab-btn'+(activeTab==='report'?' active':'')+'" data-tab="report">📊 Report<span class="tab-count">pie</span></button>';
  el.querySelectorAll('.tab-btn').forEach(function(btn){
    btn.addEventListener('click', function(){ activeTab=btn.dataset.tab; buildTabbar(); renderSlide(); window.scrollTo({top:0,behavior:'smooth'}); });
  });
}

/* ================= rendering ================= */
function canProceed(item){ return item.status==='correct'||item.status==='revealed'||item.status==='skipped'; }

function renderSlide(){
  if(!state.tabs[activeTab]){ activeTab=TAB_DEFS[0].id; }
  var ts = state.tabs[activeTab];
  var slides = SLIDES[activeTab];
  if(ts.idx>=slides.length||ts.idx<0) ts.idx=0;
  var idx = ts.idx;
  var slide = slides[idx];
  var item = ts.items[idx];

  var tdef=TAB_DEFS.find(function(t){return t.id===activeTab;});
  document.getElementById('spLabel').textContent = tdef.label+' · Question '+(idx+1)+' of '+slides.length;
  document.getElementById('secSub').textContent = tdef.label+' — '+tdef.sub;
  document.getElementById('spFill').style.width = Math.round(((idx)/(Math.max(slides.length-1,1)))*100)+'%';

  var h='<div class="qcard">';
  if(slide.kind==='mcq' || slide.kind==='ar'){
    h += renderChoiceBody(slide, item, idx);
  } else {
    h += renderBlankBody(slide, item, idx);
  }
  h += '<div class="feedback" id="feedbackBox"></div>';
  if(MODE==='learning' && (item.status==='correct'||item.status==='revealed')) h += solutionHTML(slide);
  h += '</div>';

  document.getElementById('wrap').innerHTML = h;
  wireSlideEvents(slide, item, idx);
  restoreFeedback(item);
  renderNavbar(item);
  updateFab();
  saveState();
}

function solutionHTML(slide){
  if(!slide.sol) return '';
  return '<div class="solution"><div class="sol-h">Solution</div>'+slide.sol.split('\n').map(function(l){ return '<div class="sol-line">'+fr(esc(l))+'</div>'; }).join('')+'</div>';
}
var LETTERS=['a','b','c','d','e','f'];
function chosenHTML(slide,item){
  var opts = slide.kind==='mcq' ? slide.opts : AR_OPTIONS;
  if(item.choice===undefined) return '';
  var ok=item.choice===slide.correct;
  var h='<div class="chosen '+(ok?'ok':'bad')+'"><b>Your answer:</b> ('+LETTERS[item.choice]+') '+fr(esc(opts[item.choice]))+(ok?' ✓':' ✗')+'</div>';
  if(!ok) h+='<div class="chosen ok"><b>Correct answer:</b> ('+LETTERS[slide.correct]+') '+fr(esc(opts[slide.correct]))+'</div>';
  return h;
}
function renderChoiceBody(slide, item, idx){
  var h='<div class="qhead"><div class="qnum">'+(idx+1)+'</div>';
  if(slide.kind==='mcq'){
    h += '<div class="qtext">'+fr(esc(slide.text))+(slide.tag?'<span class="qtag">'+esc(slide.tag)+'</span>':'')+'</div>';
  } else {
    h += '<div class="qtext"><span class="qtag" style="margin-left:0;margin-right:6px;">A / R</span>Assertion (A): '+fr(esc(slide.a))+'<br>Reason (R): '+fr(esc(slide.r))+(slide.tag?'<span class="qtag">'+esc(slide.tag)+'</span>':'')+'</div>';
  }
  h += '</div>';
  if(slide.fig) h += '<div class="fig">'+slide.fig+'</div>';
  var opts = slide.kind==='mcq' ? slide.opts : AR_OPTIONS;
  if(MODE==='quiz') h += '<div class="quiz-hint">Quiz mode — pick an option. The correct answer is revealed once you finish this tab.</div>';
  var locked = MODE==='learning' && (item.status==='correct' || item.status==='revealed');
  h += '<div class="options">';
  opts.forEach(function(opt,i){
    var cls='opt';
    if(locked){
      if(i===slide.correct) cls+=' is-correct';
      else if(item.choice===i) cls+=' is-wrong';
      cls+=' locked';
    }
    if(item.choice===i) cls+=' is-chosen';
    h += '<label class="'+cls+'"><input type="radio" name="choice" value="'+i+'" '+(item.choice===i?'checked':'')+' '+(locked?'disabled':'')+'> <span class="opt-l">('+LETTERS[i]+')</span> <span class="opt-t">'+fr(esc(opt))+'</span>'+(item.choice===i?'<span class="opt-tag">'+(locked?(i===slide.correct?'Your answer ✓':'Your answer ✗'):'Selected')+'</span>':'')+'</label>';
  });
  h += '</div>';
  if(locked) h += chosenHTML(slide,item);
  return h;
}

function renderBlankBody(slide, item, idx){
  var h='<div class="qhead"><div class="qnum">'+(idx+1)+'</div><div class="qtext">';
  if(slide.kind==='case'){ h += '<b>'+esc(slide.title)+'.</b> '+esc(slide.body); }
  else { var pp=fr(esc(slide.p)).split('\n'); h += pp[0]+pp.slice(1).map(function(x){return '<span class="datline">'+x+'</span>';}).join(''); }
  h += (slide.tag?'<span class="qtag">'+esc(slide.tag)+'</span>':'')+'</div>';
  if(slide.marks) h += '<div class="marks-pill">'+slide.marks+'</div>';
  h += '</div>';
  if(slide.fig) h += '<div class="fig">'+slide.fig+'</div>';

  var total = slide.flat.length;
  var hasExpr = slide.flat.some(function(s){ return s.expr===true; });
  var hasFrac = slide.flat.some(function(s){ return ['fv','fe','fl','fm','fi','flist'].indexOf(s.expr)>=0; });
  var blankCount=0; slide.flat.forEach(function(s){ blankCount+=Object.keys(s.a).length; });

  if(MODE==='quiz'){
    h += '<div class="step-badge">'+blankCount+' blank'+(blankCount===1?'':'s')+' in this question</div>';
    h += '<div class="quiz-hint">Quiz mode — fill in what you can. Correct answers are revealed once you finish this tab.</div>';
    if(hasFrac) h += '<div class="quiz-hint">Type fractions like <b>3/4</b> and mixed numbers like <b>2 3/4</b> (whole number, space, fraction).</div>';
    if(hasExpr) h += '<div class="quiz-hint">Type answers like <b>2x-5</b>, <b>x^2-4</b> or <b>3+2i</b>. Use ^ for powers, | | for absolute value and pi for π. Any equivalent form is accepted.</div>';
    h += '<div class="steps">';
    for(var qi=0; qi<total; qi++){
      var qstep = slide.flat[qi];
      var qss = item.stepStates[qi];
      if(qstep.partLabel) h += '<div class="subpart-label">'+esc(qstep.partLabel)+'</div>';
      if(qstep.orDivider) h += '<div class="or-divider">OR</div>';
      var qline = fr(qstep.t);
      Object.keys(qstep.a).forEach(function(bkey){
        var val = qss.inputs[bkey]||'';
        var inp='<input class="blank-input'+(['fv','fe','fl','fm','fi','dec'].indexOf(qstep.expr)>=0?' fr':(qstep.expr==='flist'||qstep.expr==='dlist'||qstep.expr==='glist')?' wide':qstep.expr===true?' expr':(qstep.expr==='words'||qstep.expr==='list'||qstep.expr==='expanded'||qstep.expr==='set'||qstep.expr==='primes'||qstep.expr==='trans'||qstep.expr==='rot'?' wide':''))+'" data-step="'+qi+'" data-bkey="'+bkey+'" value="'+esc(val)+'">';
        qline = qline.replace('__'+bkey+'__', inp);
      });
      if(qstep.fig) h += '<div class="fig">'+qstep.fig+'</div>';
      h += '<div class="step-line">'+qline+'</div>';
    }
    h += '</div>';
    return h;
  }

  if(hasFrac) h += '<div class="quiz-hint">Type fractions like <b>3/4</b> and mixed numbers like <b>2 3/4</b> (whole number, space, fraction).</div>';
  if(hasExpr) h += '<div class="quiz-hint">Type answers like <b>2x-5</b>, <b>x^2-4</b> or <b>3+2i</b>. Use ^ for powers, | | for absolute value and pi for π. Any equivalent form is accepted.</div>';
  var locked = item.status==='correct' || item.status==='revealed';
  var upto = locked ? total-1 : item.curStep;
  h += '<div class="step-badge">Step '+(Math.min(item.curStep,total-1)+1)+' of '+total+'</div>';
  h += '<div class="steps">';
  for(var i=0;i<=upto;i++){
    var step = slide.flat[i];
    var ss = item.stepStates[i];
    if(step.partLabel) h += '<div class="subpart-label">'+esc(step.partLabel)+'</div>';
    if(step.orDivider) h += '<div class="or-divider">OR</div>';
    var resolved = ss.status==='correct' || ss.status==='revealed';
    var line = fr(step.t);
    Object.keys(step.a).forEach(function(bkey){
      var fs = ss.inputs['fs_'+bkey];
      var cls = fs==='correct'?'is-correct':(fs==='wrong'?'is-wrong':'');
      var val = ss.inputs[bkey]||'';
      var dis = resolved ? 'disabled':'';
      var inp='<input class="blank-input '+cls+(['fv','fe','fl','fm','fi','dec'].indexOf(step.expr)>=0?' fr':(step.expr==='flist'||step.expr==='dlist'||step.expr==='glist')?' wide':step.expr===true?' expr':(step.expr==='words'||step.expr==='list'||step.expr==='expanded'||step.expr==='set'||step.expr==='primes'||step.expr==='trans'||step.expr==='rot'?' wide':''))+'" data-step="'+i+'" data-bkey="'+bkey+'" value="'+esc(val)+'" '+dis+'>';
      line = line.replace('__'+bkey+'__', inp);
    });
    if(step.fig) h += '<div class="fig">'+step.fig+'</div>';
    h += '<div class="step-line'+(resolved?' resolved':'')+'">'+line+'</div>';
    if(ss.status==='revealed'){
      var reveals=[];
      Object.keys(step.a).forEach(function(bkey){ reveals.push(bkey+' = '+esc(step.a[bkey])); });
      h += '<div class="reveal-note">correct: '+reveals.join(', ')+'</div>';
    }
  }
  h += '</div>';
  return h;
}

var __flash=null;
function restoreFeedback(item){
  var fb=document.getElementById('feedbackBox'); if(!fb) return;
  if(__flash){ fb.className='feedback show '+__flash.c; fb.innerHTML=__flash.h; __flash=null; return; }
  if(MODE==='quiz'){ fb.className='feedback'; fb.innerHTML=''; return; }
  if(item.status==='correct'){ fb.className='feedback show ok'; fb.innerHTML='<b>All done — correct!</b>'; }
  else if(item.status==='revealed'){ fb.className='feedback show reveal'; fb.innerHTML='<b>Answer revealed above.</b> Move on whenever you’re ready.'; }
  else if(item.status==='skipped'){ fb.className='feedback show retry'; fb.innerHTML='Skipped — you can answer it now and press <b>Check</b>, or come back later from the Question Palette.'; }
  else { fb.className='feedback'; fb.innerHTML=''; }
}

function slideIsAnswered(slide,item){
  if(slide.kind==='mcq'||slide.kind==='ar') return item.choice!==undefined;
  return item.stepStates.some(function(ss){ return Object.keys(ss.inputs).some(function(k){ return k.indexOf('fs_')!==0 && ss.inputs[k] && String(ss.inputs[k]).trim()!==''; }); });
}
function renderNavbar(item){
  var ts = state.tabs[activeTab];
  var slides = SLIDES[activeTab];
  var slide = slides[ts.idx];
  var isLast = ts.idx === slides.length-1;
  var h='';
  h += '<button class="btn" id="btnPrev" '+(ts.idx===0?'disabled':'')+'>&larr; Previous</button>';

  if(MODE==='quiz'){
    h += '<button class="btn" id="btnSkip">Skip</button>';
    h += '<span class="spacer"></span>';
    h += '<button class="btn btn-primary" id="btnNext">'+(isLast?'Finish':'Next →')+'</button>';
  } else {
    h += '<button class="btn" id="btnSkip" '+(item.status!=='unanswered'?'disabled':'')+'>Skip</button>';
    h += '<span class="spacer"></span>';
    h += '<button class="btn btn-primary" id="btnCheck" '+((item.status!=='unanswered'&&item.status!=='skipped')?'disabled':'')+'>Check</button>';
    h += '<button class="btn btn-primary" id="btnNext" '+(canProceed(item)?'':'disabled')+'>'+(isLast?'Finish':'Next →')+'</button>';
  }
  document.getElementById('navbarInner').innerHTML = h;

  document.getElementById('btnPrev').addEventListener('click', function(){ if(ts.idx>0){ ts.idx--; renderSlide(); } });

  if(MODE==='quiz'){
    document.getElementById('btnSkip').addEventListener('click', function(){
      item.status='skipped';
      advanceQuiz(ts, slides);
    });
    document.getElementById('btnNext').addEventListener('click', function(){
      item.status = slideIsAnswered(slide,item) ? 'answered' : 'unanswered';
      advanceQuiz(ts, slides);
    });
  } else {
    document.getElementById('btnSkip').addEventListener('click', function(){
      if(item.status==='unanswered'){ item.status='skipped'; renderSlide(); }
    });
    document.getElementById('btnNext').addEventListener('click', function(){
      if(!canProceed(item)) return;
      if(ts.idx < slides.length-1){ ts.idx++; ts.maxReached=Math.max(ts.maxReached, ts.idx); renderSlide(); }
      else { renderFinished(); }
    });
    document.getElementById('btnCheck').addEventListener('click', function(){ handleCheck(); });
  }
}
function advanceQuiz(ts, slides){
  if(ts.idx < slides.length-1){ ts.idx++; ts.maxReached=Math.max(ts.maxReached, ts.idx); renderSlide(); }
  else { renderFinished(); }
}

function wireSlideEvents(slide, item, idx){
  document.querySelectorAll('input[type="radio"][name="choice"]').forEach(function(r){
    r.addEventListener('change', function(){ item.choice=parseInt(r.value,10); saveState();
      document.querySelectorAll('.opt').forEach(function(l){ l.classList.remove('is-chosen'); var t=l.querySelector('.opt-tag'); if(t) t.remove(); });
      var lab=r.closest('.opt'); lab.classList.add('is-chosen'); var tg=document.createElement('span'); tg.className='opt-tag'; tg.textContent='Selected'; lab.appendChild(tg); });
  });
  document.querySelectorAll('.blank-input').forEach(function(inp){
    inp.addEventListener('input', function(){
      var si=parseInt(inp.dataset.step,10), bk=inp.dataset.bkey;
      item.stepStates[si].inputs[bk]=inp.value;
      saveState();
    });
  });
}

function handleCheck(){
  var ts = state.tabs[activeTab];
  var slide = SLIDES[activeTab][ts.idx];
  var item = ts.items[ts.idx];
  if(item.status==='skipped') item.status='unanswered';
  var fb = document.getElementById('feedbackBox');

  if(slide.kind==='mcq' || slide.kind==='ar'){
    if(item.choice===undefined){ fb.className='feedback show err'; fb.innerHTML='Please choose an option first.'; return; }
    var ok = item.choice===slide.correct;
    if(ok){
      item.status='correct'; playSuccess();
      fb.className='feedback show ok'; fb.innerHTML='<b>Correct!</b>';
    } else {
      item.attempts=(item.attempts||0)+1;
      if(item.attempts>=2){ item.status='revealed'; playReveal(); }
      else { playWrong(); fb.className='feedback show retry'; fb.innerHTML='<b>Not quite — try again</b> (attempt 1 of 2) <span class="attempts-dots"><span class="used"></span><span></span></span>'; __flash={c:'retry',h:'<b>Not quite — try again</b> (attempt 1 of 2) <span class="attempts-dots"><span class="used"></span><span></span></span>'}; }
    }
    renderSlide();
    return;
  }

  // blank / case
  var step = slide.flat[item.curStep];
  var ss = item.stepStates[item.curStep];
  var blanks = Object.keys(step.a);
  var missing = blanks.some(function(k){ return !ss.inputs[k] || String(ss.inputs[k]).trim()===''; });
  if(missing){ fb.className='feedback show err'; fb.innerHTML='Fill in every blank in this step before checking.'; return; }

  var allGood=true;
  blanks.forEach(function(k){
    var good=answerMatches(ss.inputs[k], step.a[k], step.accept, step.expr);
    ss.inputs['fs_'+k]=good?'correct':'wrong';
    if(!good) allGood=false;
  });

  if(allGood){
    ss.status='correct'; playSuccess();
    advanceStepOrFinish(item, slide);
  } else {
    ss.attempts=(ss.attempts||0)+1;
    if(ss.attempts>=2){
      ss.status='revealed'; playReveal();
      advanceStepOrFinish(item, slide);
    } else {
      playWrong();
      fb.className='feedback show retry';
      fb.innerHTML='<b>Not quite — try again</b> (attempt 1 of 2) <span class="attempts-dots"><span class="used"></span><span></span></span>'; __flash={c:'retry',h:'<b>Not quite — try again</b> (attempt 1 of 2) <span class="attempts-dots"><span class="used"></span><span></span></span>'};
      renderSlide();
      return;
    }
  }
  renderSlide();
}

function advanceStepOrFinish(item, slide){
  var total = slide.flat.length;
  var hasExpr = slide.flat.some(function(s){ return s.expr===true; });
  var hasFrac = slide.flat.some(function(s){ return ['fv','fe','fl','fm','fi','flist'].indexOf(s.expr)>=0; });
  if(item.curStep < total-1){
    item.curStep++;
  } else {
    var anyRevealed = item.stepStates.some(function(ss){ return ss.status==='revealed'; });
    item.status = anyRevealed ? 'revealed' : 'correct';
  }
}

/* ================= palette ================= */
var overlay=document.getElementById('overlay');
function statusOf(tabId,i){
  var ts=state.tabs[tabId];
  if(i>ts.maxReached) return 'locked';
  if(i===ts.idx) return 'current';
  return ts.items[i].status==='unanswered' ? 'locked' : ts.items[i].status;
}
function buildPalette(){
  var slides=SLIDES[activeTab];
  document.getElementById('paletteTitle').textContent = TAB_DEFS.find(function(t){return t.id===activeTab;}).label+' · Question palette';
  var body=document.getElementById('paletteBody');
  var html='';
  for(var i=0;i<slides.length;i++){
    html += '<div class="chip" data-status="'+statusOf(activeTab,i)+'" data-idx="'+i+'">'+(i+1)+'</div>';
  }
  body.innerHTML = html;
  body.querySelectorAll('.chip').forEach(function(chip){
    chip.addEventListener('click', function(){
      var i=parseInt(chip.dataset.idx,10);
      var ts=state.tabs[activeTab];
      if(i>ts.maxReached){ showToast('Finish the earlier questions to unlock this one.'); return; }
      ts.idx=i; closePalette(); renderSlide();
    });
  });
}
function openPalette(){ buildPalette(); overlay.classList.add('show'); }
function closePalette(){ overlay.classList.remove('show'); }
var toastTimer;
function showToast(msg){
  var t=document.getElementById('toast'); t.textContent=msg; t.classList.add('show');
  clearTimeout(toastTimer); toastTimer=setTimeout(function(){ t.classList.remove('show'); },2200);
}
document.getElementById('paletteFab').addEventListener('click', openPalette);
document.getElementById('paletteClose').addEventListener('click', closePalette);
overlay.addEventListener('click', function(e){ if(e.target===overlay) closePalette(); });

function updateFab(){
  var slides=SLIDES[activeTab];
  var done=state.tabs[activeTab].items.filter(function(it){ return it.status==='correct'||it.status==='revealed'||it.status==='skipped'; }).length;
  document.getElementById('fabBadge').textContent = done+'/'+slides.length;
}

/* ================= overall progress + finish ================= */
function updateChapterProgress(){
  var total=0, done=0;
  TAB_DEFS.forEach(function(td){
    state.tabs[td.id].items.forEach(function(it){
      total++;
      if(it.status==='correct'||it.status==='revealed'||it.status==='skipped') done++;
    });
  });
  var pct = total>0 ? Math.round((done/total)*100) : 0;
  document.getElementById('cpFill').style.width=pct+'%';
  document.getElementById('cpLabel').textContent=pct+'% complete';
}
function isSlideCorrect(tabId,i){
  var slide=SLIDES[tabId][i], item=state.tabs[tabId].items[i];
  if(slide.kind==='mcq'||slide.kind==='ar') return item.choice===slide.correct;
  return slide.flat.every(function(step,si){
    var ss=item.stepStates[si];
    return Object.keys(step.a).every(function(k){ return answerMatches(ss.inputs[k], step.a[k], step.accept, step.expr); });
  });
}
function isSlideAttempted(tabId,i){
  var slide=SLIDES[tabId][i], item=state.tabs[tabId].items[i];
  if(slide.kind==='mcq'||slide.kind==='ar') return item.choice!==undefined;
  return slide.flat.some(function(step,si){
    var ss=item.stepStates[si];
    return Object.keys(step.a).some(function(k){ return ss.inputs[k] && String(ss.inputs[k]).trim()!==''; });
  });
}
function slideLabel(slide){
  var t = slide.kind==='case' ? slide.title : (slide.kind==='ar' ? slide.a : (slide.p||slide.text||''));
  t = String(t);
  return t.length>90 ? t.slice(0,90)+'…' : t;
}
function slideAnswerText(slide, item, correctSide){
  if(slide.kind==='mcq'||slide.kind==='ar'){
    var opts = slide.kind==='mcq' ? slide.opts : AR_OPTIONS;
    if(correctSide) return '('+LETTERS[slide.correct]+') '+opts[slide.correct];
    return item.choice!==undefined ? '('+LETTERS[item.choice]+') '+opts[item.choice] : '— not attempted —';
  }
  return slide.flat.map(function(step,si){
    var ss=item.stepStates[si];
    return Object.keys(step.a).map(function(k){
      return correctSide ? step.a[k] : (ss.inputs[k] || '—');
    }).join(', ');
  }).join('  |  ');
}

function renderFinished(){
  if(MODE==='quiz'){ renderQuizResults(); return; }
  var ts=state.tabs[activeTab];
  var correct=ts.items.filter(function(i){return i.status==='correct';}).length;
  var revealed=ts.items.filter(function(i){return i.status==='revealed';}).length;
  var skipped=ts.items.filter(function(i){return i.status==='skipped';}).length;
  var h='<div class="qcard done-card"><div class="big">✨</div><h2>Tab complete</h2>';
  h+='<p style="color:var(--ink-soft);font-size:14px;">You worked through all '+ts.items.length+' questions in this tab.</p>';
  if(!ts.recorded){ ts.recorded=true; addRecord('learning', activeTab, correct, revealed, skipped, ts.items.length); }
  h+='<div class="score-pills">'+
     '<span class="score-pill" style="background:var(--success-soft);color:var(--success);">'+correct+' correct</span>'+
     '<span class="score-pill" style="background:var(--danger-soft);color:var(--danger);">'+revealed+' revealed</span>'+
     '<span class="score-pill" style="background:var(--gold-soft);color:var(--retry-text);">'+skipped+' skipped</span></div>'+
     '<button class="btn btn-primary" id="btnReview">Review from question 1</button></div>';
  document.getElementById('wrap').innerHTML=h;
  document.getElementById('navbarInner').innerHTML='';
  document.getElementById('btnReview').addEventListener('click', function(){ ts.idx=0; ts.recorded=false; renderSlide(); });
  updateChapterProgress(); saveState();
}

function renderQuizResults(){
  var ts=state.tabs[activeTab];
  var slides=SLIDES[activeTab];
  var correctCount=0, attemptedCount=0;
  var rowsHtml = slides.map(function(slide,i){
    var item=ts.items[i];
    var ok=isSlideCorrect(activeTab,i);
    var att=isSlideAttempted(activeTab,i);
    if(ok) correctCount++;
    if(att) attemptedCount++;
    var tagCls = ok?'ok':(att?'bad':'na');
    var tagText = ok?'Correct':(att?'Incorrect':'Not attempted');
    var row='<div class="review-row">';
    row+='<span class="review-tag '+tagCls+'">Q'+(i+1)+' · '+tagText+'</span>';
    row+='<div class="review-q">'+fr(esc(slideLabel(slide)))+'</div>';
    row+='<div class="review-ans"><b>Your answer:</b> '+fr(esc(slideAnswerText(slide,item,false)))+'</div>';
    if(!ok) row+='<div class="review-ans" style="color:var(--success);"><b>Correct answer:</b> '+fr(esc(slideAnswerText(slide,item,true)))+'</div>';
    if(slide.sol) row+='<details class="rev-sol"><summary>Show solution</summary>'+solutionHTML(slide)+'</details>';
    row+='</div>';
    return row;
  }).join('');

  addRecord('quiz', activeTab, correctCount, 0, 0, slides.length);
  var h='<div class="qcard done-card" style="text-align:left;">';
  h+='<div style="text-align:center;"><div class="big">🏁</div><h2>Quiz complete</h2>';
  h+='<p style="color:var(--ink-soft);font-size:14px;">'+correctCount+' / '+slides.length+' correct · '+attemptedCount+' attempted</p></div>';
  h+='<div style="margin-top:16px;">'+rowsHtml+'</div>';
  h+='<div style="text-align:center;margin-top:6px;"><button class="btn btn-primary" id="btnReview">Review from question 1</button></div>';
  h+='</div>';
  document.getElementById('wrap').innerHTML=h;
  document.getElementById('navbarInner').innerHTML='';
  document.getElementById('btnReview').addEventListener('click', function(){ ts.idx=0; renderSlide(); });
  playSuccess();
  updateChapterProgress(); saveState();
}

/* ================= mode picker ================= */
function updateModePill(){
  var btn=document.getElementById('modePill');
  if(!btn) return;
  btn.textContent = MODE==='quiz' ? '📝 Quiz Mode · switch' : '📘 Learning Sheet · switch';
}
function showChrome(show){
  document.querySelector('.tabbar').style.display = show?'':'none';
  document.querySelector('.slide-progress').style.display = show?'':'none';
  document.querySelector('.navbar').style.display = show?'':'none';
  document.getElementById('paletteFab').style.display = show?'':'none';
}
function renderModePicker(){
  showChrome(false);
  var wrap=document.getElementById('wrap');
  wrap.innerHTML =
    '<div class="mode-pick">'+
      '<div class="mode-card" data-pick="learning"><div class="mode-icon">📘</div><h3>Learning Sheet</h3>'+
      '<p>Work through each question step by step with instant feedback — two tries, then the correct value is revealed right there so you can keep moving.</p></div>'+
      '<div class="mode-card" data-pick="quiz"><div class="mode-icon">📝</div><h3>Quiz Mode</h3>'+
      '<p>Attempt every question with no hints along the way. Your score and the full answer key are shown together once you finish the tab — just like the real exam.</p></div>'+
    '</div>';
  wrap.querySelectorAll('[data-pick]').forEach(function(card){
    card.addEventListener('click', function(){
      setMode(card.dataset.pick); activeTab='theory';
      document.getElementById('modePill').hidden=false;
      updateModePill();
      showChrome(true);
      buildTabbar();
      renderSlide();
    });
  });
}
document.getElementById('modePill').addEventListener('click', function(){
  if(!appState.mode){ return; }
  setMode(appState.mode==='quiz' ? 'learning' : 'quiz');
  updateModePill();
  showChrome(true);
  buildTabbar();
  renderSlide();
});

/* ================= boot ================= */
var _origRenderSlide = renderSlide;
renderSlide = function(){ _origRenderSlide(); updateChapterProgress(); updateModePill(); };


/* ================= theory tab ================= */
function renderTheory(){
  var wrap=document.getElementById('wrap');
  wrap.innerHTML='<div class="theory">'+fr(THEORY)+'</div>';
  document.querySelector('.slide-progress').style.display='none';
  document.querySelector('.navbar').style.display='none';
  document.getElementById('paletteFab').style.display='none';
  document.getElementById('secSub').textContent='Theory — notes, key ideas and worked examples';
  wrap.querySelectorAll('[data-go]').forEach(function(b){ b.addEventListener('click',function(){ activeTab=b.dataset.go; buildTabbar(); renderSlide(); window.scrollTo({top:0,behavior:'smooth'}); }); });
  wrap.querySelectorAll('[data-jump]').forEach(function(b){ b.addEventListener('click',function(){ var t=document.getElementById(b.dataset.jump); if(t) t.scrollIntoView({behavior:'smooth',block:'start'}); }); });
}
var _rsTheory = renderSlide;
renderSlide = function(){
  if(activeTab==='theory'){ renderTheory(); buildTabbar(); updateChapterProgress(); updateModePill(); saveState(); return; }
  document.querySelector('.slide-progress').style.display='';
  document.querySelector('.navbar').style.display='';
  document.getElementById('paletteFab').style.display='';
  _rsTheory();
};


/* ================= MYP criterion report ================= */
var CRIT_COL={A:'var(--accent-text)',B:'var(--gold)',C:'#8A6FC4',D:'#2F9AA0'};
function critStats(){
  return REPORT.map(function(r){
    var tabId=r[0], slides=SLIDES[tabId], ts=state&&state.tabs[tabId];
    var c=0,w=0,n=0;
    slides.forEach(function(sl,i){
      if(!ts||!ts.items[i]){ n++; return; }
      var it=ts.items[i];
      if(MODE==='learning'){
        if(it.status==='correct') c++; else if(it.status==='revealed') w++; else n++;
      } else {
        if(isSlideCorrect(tabId,i)) c++; else if(isSlideAttempted(tabId,i)) w++; else n++;
      }
    });
    var tot=slides.length, pct=tot?Math.round(c/tot*100):0;
    var lvl=Math.round(c/Math.max(tot,1)*8);
    return {tab:tabId,letter:r[1],name:r[2],c:c,w:w,n:n,tot:tot,pct:pct,lvl:lvl};
  });
}
function arcPath(cx,cy,r,a0,a1){
  if(a1-a0>=Math.PI*2-1e-6){ return 'M'+(cx-r)+','+cy+' a'+r+','+r+' 0 1,0 '+(2*r)+',0 a'+r+','+r+' 0 1,0 '+(-2*r)+',0 Z'; }
  var x0=cx+r*Math.sin(a0), y0=cy-r*Math.cos(a0), x1=cx+r*Math.sin(a1), y1=cy-r*Math.cos(a1);
  return 'M'+cx+','+cy+' L'+x0.toFixed(2)+','+y0.toFixed(2)+' A'+r+','+r+' 0 '+((a1-a0)>Math.PI?1:0)+',1 '+x1.toFixed(2)+','+y1.toFixed(2)+' Z';
}
function pieSVG(parts,size,hole,center,sub){
  var tot=parts.reduce(function(s,p){return s+p.v;},0), cx=size/2, cy=size/2, r=size/2-4, a=0, h='';
  if(!tot){ h+='<circle cx="'+cx+'" cy="'+cy+'" r="'+r+'" style="fill:var(--paper-2);stroke:var(--rule)"/>'; }
  parts.forEach(function(p){ if(!p.v) return; var b=a+p.v/tot*Math.PI*2; h+='<path d="'+arcPath(cx,cy,r,a,b)+'" style="fill:'+p.col+';stroke:var(--card);stroke-width:2"><title>'+esc(p.label)+': '+p.v+'</title></path>'; a=b; });
  if(hole) h+='<circle cx="'+cx+'" cy="'+cy+'" r="'+(r*hole)+'" style="fill:var(--card)"/>';
  if(center) h+='<text x="'+cx+'" y="'+(cy-(sub?4:0))+'" text-anchor="middle" dominant-baseline="middle" style="fill:var(--ink);font:700 '+(size>150?22:15)+'px Fraunces,serif">'+center+'</text>';
  if(sub) h+='<text x="'+cx+'" y="'+(cy+16)+'" text-anchor="middle" style="fill:var(--ink-soft);font:600 11px \'Source Sans 3\',sans-serif">'+sub+'</text>';
  return '<svg viewBox="0 0 '+size+' '+size+'" width="'+size+'" height="'+size+'" role="img">'+h+'</svg>';
}
function band(l){ return l===0?'0':(l<=2?'1–2':(l<=4?'3–4':(l<=6?'5–6':'7–8'))); }
function renderReport(){
  var st=critStats(), totC=0, totQ=0;
  st.forEach(function(s){ totC+=s.c; totQ+=s.tot; });
  var h='<div class="theory">';
  h+='<section class="note"><h2>Chapter test report</h2><p class="lt">'+(MODE==='quiz'?'<b>Quiz mode</b> results: answers are marked when you finish each test tab.':'<b>Learning mode</b> results: a question counts as correct only if you got it without the answer being revealed. Switch to Quiz mode for an exam-style score.')+'</p>';
  h+='<div class="rep-top"><div class="rep-pie">'+pieSVG(st.map(function(s){return {v:s.c,col:CRIT_COL[s.letter],label:'Criterion '+s.letter};}),200,0.55,totC+'/'+totQ,'correct')+'</div>';
  h+='<div class="rep-legend"><div class="rep-cap">Marks earned, by criterion</div>'+st.map(function(s){ return '<div class="rep-li"><span class="sw" style="background:'+CRIT_COL[s.letter]+'"></span><b>'+s.letter+'</b>&nbsp;'+esc(s.name)+'<span class="rep-n">'+s.c+' / '+s.tot+'</span></div>'; }).join('')+'</div></div></section>';
  h+='<div class="rep-grid">'+st.map(function(s){
    return '<div class="rep-card"><div class="rep-h"><span class="crit" style="background:'+CRIT_COL[s.letter]+'">'+s.letter+'</span>'+esc(s.name)+'</div>'+
      '<div class="rep-row">'+pieSVG([{v:s.c,col:'var(--success)',label:'Correct'},{v:s.w,col:'var(--danger)',label:'Incorrect'},{v:s.n,col:'var(--locked)',label:'Not attempted'}],120,0.5,s.pct+'%')+
      '<div class="rep-stats"><div><span class="sw" style="background:var(--success)"></span>Correct <b>'+s.c+'</b></div><div><span class="sw" style="background:var(--danger)"></span>Incorrect <b>'+s.w+'</b></div><div><span class="sw" style="background:var(--locked)"></span>Not attempted <b>'+s.n+'</b></div>'+
      '<div class="rep-lvl">Indicative level <b>'+s.lvl+'</b> / 8 <span>(band '+band(s.lvl)+')</span></div></div></div>'+
      '<button class="hub-btn" data-go="'+s.tab+'">Open Test '+s.letter+' →</button></div>';
  }).join('')+'</div>';
  h+='<p class="rep-note">Indicative level = fraction of questions correct × 8, rounded. It is a practice guide only; your teacher awards the real MYP criterion levels.</p></div>';
  var wrap=document.getElementById('wrap'); wrap.innerHTML=h;
  document.querySelector('.slide-progress').style.display='none';
  document.querySelector('.navbar').style.display='none';
  document.getElementById('paletteFab').style.display='none';
  document.getElementById('secSub').textContent='Report — chapter test results by MYP criterion';
  wrap.querySelectorAll('[data-go]').forEach(function(b){ b.addEventListener('click',function(){ activeTab=b.dataset.go; buildTabbar(); renderSlide(); window.scrollTo({top:0,behavior:'smooth'}); }); });
}
var _rsReport = renderSlide;
renderSlide = function(){
  if(activeTab==='report'){ renderReport(); buildTabbar(); updateChapterProgress(); updateModePill(); saveState(); return; }
  _rsReport();
};


/* ================= skipped-question return ================= */
function firstSkippedIdx(ts){
  for(var i=0;i<ts.items.length;i++){
    var it=ts.items[i];
    if(MODE==='quiz'){ if(!isSlideAttempted(activeTab,i)) return i; }
    else if(it.status==='skipped'||it.status==='unanswered') return i;
  }
  return -1;
}
function skippedList(ts){
  var out=[]; for(var i=0;i<ts.items.length;i++){ var it=ts.items[i];
    if(MODE==='quiz' ? !isSlideAttempted(activeTab,i) : (it.status==='skipped'||it.status==='unanswered')) out.push(i); }
  return out;
}
function renderSkipGate(ts){
  var list=skippedList(ts);
  var h='<div class="qcard done-card"><div class="big">⏭️</div><h2>You skipped '+list.length+' question'+(list.length>1?'s':'')+'</h2>'+
    '<p style="color:var(--ink-soft);font-size:14px;">Answer them now, or submit the tab as it is. Answers are marked only when you submit.</p>'+
    '<div class="skip-chips">'+list.map(function(i){ return '<button class="chip skip-go" data-i="'+i+'">Q'+(i+1)+'</button>'; }).join('')+'</div>'+
    '<div class="skip-btns"><button class="btn btn-primary" id="btnGoSkipped">Answer skipped questions</button><button class="btn" id="btnSubmitAnyway">Submit anyway</button></div></div>';
  document.getElementById('wrap').innerHTML=h;
  document.getElementById('navbarInner').innerHTML='';
  var go=function(i){ ts.idx=i; ts.maxReached=Math.max(ts.maxReached,i); renderSlide(); window.scrollTo({top:0,behavior:'smooth'}); };
  document.getElementById('btnGoSkipped').addEventListener('click',function(){ go(list[0]); });
  document.querySelectorAll('.skip-go').forEach(function(b){ b.addEventListener('click',function(){ go(parseInt(b.dataset.i,10)); }); });
  document.getElementById('btnSubmitAnyway').addEventListener('click',function(){ ts.submitOK=true; renderFinished(); ts.submitOK=false; });
  saveState();
}
var _rfSkip = renderFinished;
renderFinished = function(){
  var ts=state.tabs[activeTab];
  if(MODE==='quiz' && !ts.submitOK && skippedList(ts).length){ renderSkipGate(ts); return; }
  _rfSkip();
  if(MODE==='learning'){
    var list=skippedList(ts);
    if(list.length){
      var card=document.querySelector('.done-card');
      if(card){ var d=document.createElement('div'); d.className='skip-btns';
        d.innerHTML='<button class="btn btn-primary" id="btnGoSkipped">Attempt skipped questions ('+list.length+')</button>';
        card.appendChild(d);
        document.getElementById('btnGoSkipped').addEventListener('click',function(){ ts.idx=list[0]; ts.recorded=false; renderSlide(); window.scrollTo({top:0,behavior:'smooth'}); }); }
    }
  }
};


/* ================= approx answers (physics: within 1%) ================= */
var _amTools = answerMatches;
answerMatches = function(input,answer,accept,expr){
  if(expr==='approx'){
    var n1=parseNum(input); if(n1===null) return false;
    return [answer].concat(accept||[]).some(function(a){ var n2=parseNum(a); if(n2===null) return false; return Math.abs(n1-n2) <= Math.max(0.011*Math.abs(n2), 1e-9); });
  }
  return _amTools(input,answer,accept,expr);
};

/* ================= palette: every question already reached can be opened ================= */
statusOf = function(tabId,i){
  var ts=state.tabs[tabId];
  if(i>ts.maxReached) return 'locked';
  if(i===ts.idx) return 'current';
  var s=ts.items[i].status;
  if(s==='unanswered') return 'skipped';
  return s;
};

/* ================= on-screen keyboard ================= */
var KB={on:true, page:'num', target:null};
try{ var kbp=localStorage.getItem('sopaan-kb-pref'); if(kbp==='off') KB.on=false; }catch(e){}
function kbSave(){ try{ localStorage.setItem('sopaan-kb-pref', KB.on?'on':'off'); }catch(e){} }
var KEYS_NUM=[['7','8','9','(',')'],['4','5','6','−','/'],['1','2','3','.',','],['0',':','%','°','⌫'],['abc','←','→','Clear','Done']];
var KEYS_FRAC=[['7','8','9','/'],['4','5','6','−'],['1','2','3','space'],['0',',','⌫','Clear'],['abc','←','→','Done']];
var KEYS_ALG=[['7','8','9','x','y','n'],['4','5','6','+','−','a'],['1','2','3','×','÷','b'],['0','.','(',')','^','²'],['/','π','|','t','⌫','Clear'],['abc','←','→','Done']];
function kbLayoutFor(inp){ try{ var ts=state.tabs[activeTab], sl=SLIDES[activeTab][ts.idx], stp=sl.flat[parseInt(inp.dataset.step,10)]; var m=stp.expr, key=String(stp.a[inp.dataset.bkey]||'');
  if(m==='words'||m==='glist'||m==='angle') return 'abc'; if(m===true||m==='pow'||m==='primes') return 'alg';
  if(['fv','fe','fl','fm','fi','flist'].indexOf(m)>=0) return 'frac'; if(m==='dec'||m==='approx'||m==='dlist'||m==='set'||m==='coord'||m==='list'||m==='time') return 'num';
  if(/^[\-−]?\d+ \d+\/\d+$/.test(key)||/^[\-−]?\d+\/\d+$/.test(key)) return 'frac'; if(/[a-df-z]/i.test(key.replace(/pi/gi,''))) return /\d/.test(key)?'alg':'abc'; return 'num'; }catch(e){ return 'num'; } }
var KEYS_ABC=[['q','w','e','r','t','y','u','i','o','p'],['a','s','d','f','g','h','j','k','l','-'],['z','x','c','v','b','n','m',',',':','/'],['123','space','←','→','⌫','Done']];
function kbBuild(){
  var el=document.getElementById('vkb'); if(!el){ el=document.createElement('div'); el.id='vkb'; el.className='vkb'; document.body.appendChild(el);
    el.addEventListener('pointerdown',function(e){ var b=e.target.closest('button[data-k]'); e.preventDefault(); if(b) kbPress(b.dataset.k); });
    el.addEventListener('mousedown',function(e){ e.preventDefault(); }); }
  var rows={num:KEYS_NUM,frac:KEYS_FRAC,alg:KEYS_ALG,abc:KEYS_ABC}[KB.page]||KEYS_NUM;
  el.innerHTML='<div class="vkb-top"><span>⌨️ Keyboard</span><button data-k="device" class="vkb-link">Use device keyboard</button></div>'+
    rows.map(function(r){ return '<div class="vkb-row">'+r.map(function(k){
      var cls='vkb-k'+(/^(abc|123|Done|Clear|⌫|←|→|space)$/.test(k)?' fn':'')+(k==='Done'?' done':'');
      return '<button type="button" class="'+cls+'" data-k="'+k+'">'+(k==='space'?'space':k)+'</button>'; }).join('')+'</div>'; }).join('');
  return el;
}
function kbShow(inp){ KB.target=inp; KB.home=kbLayoutFor(inp); KB.page=KB.home; if(!KB.on) return; var cp=document.getElementById('calcPanel'); if(cp&&cp.classList.contains('show')) return; var el=kbBuild(); var nb=document.querySelector('.navbar'); el.style.bottom=(nb?nb.getBoundingClientRect().height:0)+'px'; el.classList.add('show'); document.body.classList.add('kb-open'); setTimeout(function(){ var r=inp.getBoundingClientRect(), top=el.getBoundingClientRect().top; if(r.bottom>top-12) window.scrollBy({top:r.bottom-top+60,behavior:'smooth'}); else if(r.top<60) window.scrollBy({top:r.top-80,behavior:'smooth'}); },30); }
function kbHide(){ var el=document.getElementById('vkb'); if(el) el.classList.remove('show'); document.body.classList.remove('kb-open'); }
function kbInsert(s){
  var t=KB.target; if(!t||t.disabled) return;
  var a=t.selectionStart==null?t.value.length:t.selectionStart, b=t.selectionEnd==null?a:t.selectionEnd;
  t.value=t.value.slice(0,a)+s+t.value.slice(b); var p=a+s.length; try{ t.setSelectionRange(p,p); }catch(e){}
  t.dispatchEvent(new Event('input',{bubbles:true}));
}
function kbPress(k){
  var t=KB.target; if(k==='device'){ KB.on=false; kbSave(); kbHide(); document.querySelectorAll('.blank-input').forEach(function(i){ i.removeAttribute('inputmode'); }); if(t){ t.blur(); setTimeout(function(){ t.focus(); },50); } showToast('Device keyboard on. Tap ⌨️ on any blank to bring the on-screen keyboard back.'); return; }
  if(k==='Done'){ kbHide(); if(t) t.blur(); return; }
  if(k==='abc'||k==='123'){ KB.page=(k==='abc')?'abc':(KB.home&&KB.home!=='abc'?KB.home:'num'); kbBuild(); return; }
  if(!t) return;
  if(k==='⌫'){ var a=t.selectionStart, b=t.selectionEnd; if(a===b&&a>0){ t.value=t.value.slice(0,a-1)+t.value.slice(b); try{t.setSelectionRange(a-1,a-1);}catch(e){} } else { t.value=t.value.slice(0,a)+t.value.slice(b); try{t.setSelectionRange(a,a);}catch(e){} } t.dispatchEvent(new Event('input',{bubbles:true})); return; }
  if(k==='Clear'){ t.value=''; t.dispatchEvent(new Event('input',{bubbles:true})); return; }
  if(k==='←'||k==='→'){ var p=(t.selectionStart||0)+(k==='←'?-1:1); p=Math.max(0,Math.min(t.value.length,p)); try{t.setSelectionRange(p,p);}catch(e){} return; }
  var map={'−':'-','space':' '}; kbInsert(map[k]!==undefined?map[k]:k);
}
function kbWire(){
  document.querySelectorAll('.blank-input').forEach(function(inp){
    if(inp.dataset.kb) return; inp.dataset.kb='1';
    if(KB.on) inp.setAttribute('inputmode','none');
    inp.addEventListener('focus',function(){ kbShow(inp); });
    var btn=document.createElement('button'); btn.type='button'; btn.className='kb-toggle'; btn.title='On-screen keyboard'; btn.textContent='⌨️'; btn.tabIndex=-1;
    btn.addEventListener('mousedown',function(e){ e.preventDefault(); });
    btn.addEventListener('click',function(){ KB.on=true; kbSave(); document.querySelectorAll('.blank-input').forEach(function(i){ i.setAttribute('inputmode','none'); }); inp.focus(); kbShow(inp); });
    if(!inp.disabled) inp.insertAdjacentElement('afterend',btn);
  });
}
document.addEventListener('focusout',function(e){ setTimeout(function(){ var a=document.activeElement; if(!a||!a.classList||!a.classList.contains('blank-input')){ if(!document.querySelector('#vkb:hover')) kbHide(); } },120); });

/* ================= calculator ================= */
var CALC={expr:'', ans:0};
function calcEval(src){
  var s=String(src).replace(/×/g,'*').replace(/÷/g,'/').replace(/−/g,'-').replace(/π/g,'(PI)').replace(/Ans/g,'('+CALC.ans+')').replace(/\^/g,'**').replace(/√\(/g,'sqrt(').replace(/²/g,'**2').replace(/E/g,'*10**');
  s=s.replace(/(^|[(*\/+\-,])-/g,'$1(-1)*');
  if(/[^0-9+\-*/().,a-z A-Z]/.test(s)) throw 0;
  var ok=s.replace(/sin|cos|tan|asin|acos|atan|sqrt|log|ln|PI|abs/g,''); if(/[a-zA-Z]/.test(ok)) throw 0;
  var f=new Function('sin','cos','tan','asin','acos','atan','sqrt','log','ln','PI','abs','return ('+s+');');
  var d=Math.PI/180;
  var v=f(function(x){return Math.sin(x*d);},function(x){return Math.cos(x*d);},function(x){return Math.tan(x*d);},
    function(x){return Math.asin(x)/d;},function(x){return Math.acos(x)/d;},function(x){return Math.atan(x)/d;},Math.sqrt,Math.log10,Math.log,Math.PI,Math.abs);
  if(typeof v!=='number'||!isFinite(v)) throw 0; return v;
}
function fmtNum(v){ if(Math.abs(v)>=1e10||(Math.abs(v)<1e-6&&v!==0)) return v.toExponential(6).replace(/\.?0+e/,'e'); return String(parseFloat(v.toPrecision(10))); }
var CKEYS=[['sin(','cos(','tan(','√(','^','²'],['asin(','acos(','atan(','(',')','π'],['7','8','9','÷','⌫','AC'],['4','5','6','×','E','Ans'],['1','2','3','−','(−)','Insert'],['0','.','=','+']];
function openCalc(){
  var p=document.getElementById('calcPanel');
  if(!p){ p=document.createElement('div'); p.id='calcPanel'; p.className='tool-panel calc';
    p.innerHTML='<div class="tp-head"><b>🧮 Calculator</b><span class="tp-note">degrees · tap a blank, then Insert</span><button class="tp-x" data-c="close">✕</button></div>'+
      '<div class="calc-disp"><div class="calc-expr" id="calcExpr"></div><div class="calc-res" id="calcRes">0</div></div>'+
      '<div class="calc-keys">'+CKEYS.map(function(r){ return r.map(function(k){ return '<button type="button" data-c="'+k+'" class="'+(k==='='?'eq':(/^(AC|⌫|Insert)$/.test(k)?'fn':''))+'">'+({'sin(':'sin','cos(':'cos','tan(':'tan','asin(':'sin⁻¹','acos(':'cos⁻¹','atan(':'tan⁻¹','√(':'√'}[k]||k)+'</button>'; }).join(''); }).join('')+'</div>';
    document.body.appendChild(p);
    p.addEventListener('mousedown',function(e){ if(e.target.closest('button')) e.preventDefault(); });
    p.addEventListener('click',function(e){ var b=e.target.closest('button[data-c]'); if(!b) return; calcKey(b.dataset.c); });
  }
  kbHide(); var nb=document.querySelector('.navbar'); p.style.bottom=((nb?nb.getBoundingClientRect().height:0)+8)+'px'; p.classList.add('show'); document.body.classList.add('calc-open'); calcShow();
}
function calcShow(res){ document.getElementById('calcExpr').textContent=CALC.expr||' '; if(res!==undefined) document.getElementById('calcRes').textContent=res; }
function calcKey(k){
  if(k==='close'){ document.getElementById('calcPanel').classList.remove('show'); document.body.classList.remove('calc-open'); return; }
  if(k==='AC'){ CALC.expr=''; calcShow('0'); return; }
  if(k==='⌫'){ CALC.expr=CALC.expr.replace(/(asin\(|acos\(|atan\(|sin\(|cos\(|tan\(|√\(|Ans|.)$/,''); calcShow(); return; }
  if(k==='='){ try{ var v=calcEval(CALC.expr); CALC.ans=v; calcShow(fmtNum(v)); }catch(e){ calcShow('Error'); } return; }
  if(k==='(−)'){ CALC.expr+='−'; calcShow(); return; }
  if(k==='Insert'){ var r=document.getElementById('calcRes').textContent; if(KB.target && !KB.target.disabled && r!=='Error'){ KB.target.value=r; KB.target.dispatchEvent(new Event('input',{bubbles:true})); showToast('Inserted '+r+' into the blank.'); } else showToast('Tap a blank first, then press Insert.'); return; }
  CALC.expr+=k; calcShow();
}

/* ================= Desmos ================= */
var DESMOS_KEY='dcb31709b452b1cf9dc26972add0fda6', desmosCalc=null, desmosLoading=false;
function openDesmos(exprs){
  var p=document.getElementById('desmosPanel');
  if(!p){ p=document.createElement('div'); p.id='desmosPanel'; p.className='tool-panel desmos';
    p.innerHTML='<div class="tp-head"><b>📈 Desmos graphing calculator</b><button class="tp-x" id="desmosReset">Reset graph</button><button class="tp-x" id="desmosClose">✕</button></div><div id="desmosBox"><div class="desmos-msg">Loading Desmos…</div></div>';
    document.body.appendChild(p);
    document.getElementById('desmosClose').addEventListener('click',function(){ p.classList.remove('show'); });
    document.getElementById('desmosReset').addEventListener('click',function(){ if(desmosCalc) desmosSet(p._exprs||[]); });
  }
  p._exprs=exprs||[]; p.classList.add('show');
  if(window.Desmos){ desmosInit(); desmosSet(p._exprs); return; }
  if(desmosLoading) return; desmosLoading=true;
  var sc=document.createElement('script'); sc.src='https://www.desmos.com/api/v1.9/calculator.js?apiKey='+DESMOS_KEY;
  sc.onload=function(){ desmosInit(); desmosSet(p._exprs); };
  sc.onerror=function(){ desmosLoading=false; document.getElementById('desmosBox').innerHTML='<div class="desmos-msg">Desmos needs an internet connection. <a href="https://www.desmos.com/calculator" target="_blank" rel="noopener">Open Desmos in a new tab</a>.</div>'; };
  document.head.appendChild(sc);
}
function desmosInit(){ if(desmosCalc) return; var box=document.getElementById('desmosBox'); box.innerHTML=''; desmosCalc=Desmos.GraphingCalculator(box,{expressionsCollapsed:false,settingsMenu:false,border:false,degreeMode:true}); }
function desmosSet(exprs){ if(!desmosCalc) return; desmosCalc.setBlank(); (exprs||[]).forEach(function(e,i){ if(typeof e==='string') desmosCalc.setExpression({id:'e'+i,latex:e}); else desmosCalc.setExpression(Object.assign({id:'e'+i},e)); }); }

/* ================= toolbar on each question ================= */
var _rsTools = renderSlide;
renderSlide = function(){
  _rsTools();
  kbHide();
  if(activeTab==='theory'||activeTab==='report') return;
  var ts=state.tabs[activeTab]; if(!ts) return;
  var slide=SLIDES[activeTab][ts.idx], card=document.querySelector('#wrap .qcard');
  if(card && slide && slide.tools && slide.tools.length && !card.querySelector('.tool-bar')){
    var bar=document.createElement('div'); bar.className='tool-bar';
    bar.innerHTML=(slide.tools.indexOf('calc')>=0?'<button type="button" class="tool-btn" data-t="calc">🧮 Calculator</button>':'')+
                  (slide.tools.indexOf('desmos')>=0?'<button type="button" class="tool-btn" data-t="desmos">📈 Desmos graph</button>':'');
    card.insertBefore(bar, card.firstChild);
    bar.addEventListener('click',function(e){ var b=e.target.closest('[data-t]'); if(!b) return; if(b.dataset.t==='calc') openCalc(); else openDesmos(slide.desmos||[]); });
  }
  kbWire();
};



/* ================= signed fractions in text: {−3/4}, {3/−4}, {−2 1/3}, {p/q} ================= */
fr = function(s){ return String(s).replace(/&lt;(\/?)(b|sup|sub|i)>/g,'<$1$2>')
  .replace(/\{([−-]?\d+) (\d+)\/(\d+)\}/g,'<span class="mx">$1<span class="fq"><span>$2</span><span>$3</span></span></span>')
  .replace(/\{([−-]?[A-Za-z0-9]+)\/([−-]?[A-Za-z0-9]+)\}/g,'<span class="fq"><span>$1</span><span>$2</span></span>'); };
/* ================= BMA badge → main page of this sheet (theory hub) ================= */
(function(){
  var c=document.querySelector('.brand .crest'); if(!c) return;
  var a=document.createElement('button'); a.type='button'; a.className='crest crest-home'; a.title='Back to the main page (theory notes)'; a.setAttribute('aria-label','Main page');
  a.innerHTML='BM<span class="crest-h">⌂</span>'; c.parentNode.replaceChild(a,c);
  a.addEventListener('click',function(){
    if(!student||!MODE){ window.scrollTo({top:0,behavior:'smooth'}); return; }
    if(typeof kbHide==='function') kbHide(); if(typeof SP!=='undefined'&&SP.on) spToggle(false);
    var cp=document.getElementById('calcPanel'); if(cp) cp.classList.remove('show'); document.body.classList.remove('calc-open');
    activeTab = (typeof THEORY!=='undefined') ? 'theory' : TAB_DEFS[0].id;
    buildTabbar(); renderSlide(); window.scrollTo({top:0,behavior:'smooth'});
  });
})();

/* ================= session clock: starts at sign-in and keeps running ================= */
var CLK={t0:null};
(function(){
  var row=document.querySelector('.brand .brand-row'); if(!row) return;
  var d=document.createElement('div'); d.className='bmasw off'; d.id='swBox'; d.title='Time since you signed in';
  d.innerHTML='<span class="bmasw-ic">⏱</span><span class="bmasw-t" id="swT">00:00</span>';
  row.appendChild(d); setInterval(swTick,1000);
})();
function swFmt(s){ s=Math.floor(s||0); var h=Math.floor(s/3600), m=Math.floor(s%3600/60), x=s%60; return (h?h+':'+String(m).padStart(2,'0'):String(m).padStart(2,'0'))+':'+String(x).padStart(2,'0'); }
function swTick(){
  var box=document.getElementById('swBox'); if(!box) return;
  if(student && !CLK.t0) CLK.t0=Date.now();
  if(!student) CLK.t0=null;
  box.classList.toggle('off',!CLK.t0);
  document.getElementById('swT').textContent = CLK.t0 ? swFmt((Date.now()-CLK.t0)/1000) : '00:00';
}
function swTab(){ try{ if(!state||!state.tabs||activeTab==='theory'||activeTab==='report') return null; return state.tabs[activeTab]||null; }catch(e){ return null; } }
var _rsSW = renderSlide;
renderSlide = function(){ _rsSW(); swTick(); };
var _rfSW = renderFinished;
renderFinished = function(){ _rfSW(); var done=document.querySelector('#wrap .done-card'); if(CLK.t0 && done && !done.querySelector('.bmasw-done')){ var p=document.createElement('p'); p.className='bmasw-done'; p.textContent='⏱ Time since sign-in: '+swFmt((Date.now()-CLK.t0)/1000); var h2=done.querySelector('h2'); if(h2) h2.insertAdjacentElement('afterend',p); else done.appendChild(p); } };

/* ================= scratchpad (Khan-style, 4 pens) ================= */
var SP={on:false, draw:true, color:'ink', size:3, erase:false, store:{}, key:null, cv:null, ctx:null, down:false, last:null};
var SP_COL={ink:null, blue:'#2563EB', red:'#DC2626', green:'#16A34A'};
function spInk(){ return getComputedStyle(document.documentElement).getPropertyValue('--ink').trim()||'#211E1A'; }
function spKey(){ var ts=swTab(); return ts ? (MODE+'|'+activeTab+'|'+ts.idx) : null; }
function spBuild(){
  if(SP.cv) return;
  var cv=document.createElement('canvas'); cv.id='spCanvas'; cv.className='sp-canvas'; document.body.appendChild(cv);
  var bar=document.createElement('div'); bar.id='spBar'; bar.className='sp-bar';
  bar.innerHTML='<span class="sp-lbl">✏️ Scratchpad</span>'+
    ['ink','blue','red','green'].map(function(c){ return '<button type="button" class="sp-pen" data-c="'+c+'" title="'+(c==='ink'?'black':c)+' pen"><i style="background:'+(c==='ink'?'var(--ink)':SP_COL[c])+'"></i></button>'; }).join('')+
    '<button type="button" class="sp-tool" data-t="erase" title="Eraser">🧽</button><button type="button" class="sp-tool" data-t="size" title="Pen size">●</button><button type="button" class="sp-tool" data-t="scroll" title="Pause drawing to scroll or answer">✋</button>'+
    '<button type="button" class="sp-tool" data-t="clear" title="Clear page">🗑</button><button type="button" class="sp-tool" data-t="close" title="Close scratchpad">✕</button>';
  document.body.appendChild(bar);
  bar.addEventListener('click',function(e){ var b=e.target.closest('button'); if(!b) return;
    if(b.dataset.c){ SP.color=b.dataset.c; SP.erase=false; SP.draw=true; }
    else if(b.dataset.t==='erase'){ SP.erase=true; SP.draw=true; }
    else if(b.dataset.t==='size'){ SP.size = SP.size===3?6:(SP.size===6?1.5:3); b.textContent = SP.size===6?'⬤':(SP.size===1.5?'·':'●'); }
    else if(b.dataset.t==='scroll'){ SP.draw=!SP.draw; }
    else if(b.dataset.t==='clear'){ spClear(); }
    else if(b.dataset.t==='close'){ spToggle(false); return; }
    spUI(); });
  SP.cv=cv; SP.ctx=cv.getContext('2d');
  cv.addEventListener('pointerdown',function(e){ if(!SP.draw) return; e.preventDefault(); cv.setPointerCapture(e.pointerId); SP.down=true; SP.last=spPt(e); spDot(SP.last); });
  cv.addEventListener('pointermove',function(e){ if(!SP.down) return; e.preventDefault(); var p=spPt(e); spLine(SP.last,p); SP.last=p; });
  var up=function(){ if(SP.down){ SP.down=false; spSave(); } };
  cv.addEventListener('pointerup',up); cv.addEventListener('pointercancel',up); cv.addEventListener('pointerleave',up);
  window.addEventListener('resize',function(){ if(SP.on) spFit(true); });
}
function spPt(e){ var r=SP.cv.getBoundingClientRect(); return {x:e.clientX-r.left, y:e.clientY-r.top}; }
function spStyle(){ var c=SP.ctx; c.lineCap='round'; c.lineJoin='round'; c.globalCompositeOperation=SP.erase?'destination-out':'source-over'; c.strokeStyle=c.fillStyle=(SP.color==='ink'?spInk():SP_COL[SP.color]); c.lineWidth=SP.erase?22:SP.size; }
function spDot(p){ spStyle(); var c=SP.ctx; c.beginPath(); c.arc(p.x,p.y,(SP.erase?11:SP.size/2),0,Math.PI*2); c.fill(); }
function spLine(a,b){ spStyle(); var c=SP.ctx; c.beginPath(); c.moveTo(a.x,a.y); c.lineTo(b.x,b.y); c.stroke(); }
function spSave(){ if(SP.key&&SP.cv){ try{ SP.store[SP.key]=SP.cv.toDataURL(); }catch(e){} } }
function spClear(){ if(!SP.ctx) return; SP.ctx.save(); SP.ctx.setTransform(1,0,0,1,0,0); SP.ctx.clearRect(0,0,SP.cv.width,SP.cv.height); SP.ctx.restore(); if(SP.key) delete SP.store[SP.key]; }
function spFit(keep){
  var wrap=document.getElementById('wrap'); if(!wrap||!SP.cv) return;
  var r=wrap.getBoundingClientRect(), top=r.top+window.scrollY, h=Math.max(wrap.scrollHeight, window.innerHeight-r.top)+40, w=document.documentElement.clientWidth;
  var old=keep&&SP.key?SP.store[SP.key]:null, dpr=window.devicePixelRatio||1;
  SP.cv.style.top=top+'px'; SP.cv.style.left='0px'; SP.cv.style.width=w+'px'; SP.cv.style.height=h+'px';
  SP.cv.width=Math.round(w*dpr); SP.cv.height=Math.round(h*dpr); SP.ctx.setTransform(dpr,0,0,dpr,0,0);
  if(old){ var im=new Image(); im.onload=function(){ SP.ctx.save(); SP.ctx.setTransform(1,0,0,1,0,0); SP.ctx.drawImage(im,0,0); SP.ctx.restore(); }; im.src=old; }
}
function spLoad(){ spSave(); SP.key=spKey(); spFit(false); var d=SP.key&&SP.store[SP.key]; if(d){ var im=new Image(); im.onload=function(){ SP.ctx.save(); SP.ctx.setTransform(1,0,0,1,0,0); SP.ctx.drawImage(im,0,0); SP.ctx.restore(); }; im.src=d; } }
function spUI(){
  var bar=document.getElementById('spBar'); if(!bar) return;
  bar.querySelectorAll('.sp-pen').forEach(function(b){ b.classList.toggle('on', !SP.erase && SP.draw && b.dataset.c===SP.color); });
  bar.querySelector('[data-t=erase]').classList.toggle('on', SP.erase && SP.draw);
  bar.querySelector('[data-t=scroll]').classList.toggle('on', !SP.draw);
  SP.cv.classList.toggle('passive', !SP.draw);
  var fb=document.getElementById('spFab'); if(fb) fb.classList.toggle('on',SP.on);
}
function spToggle(on){
  spBuild(); SP.on=(on===undefined)?!SP.on:on;
  document.body.classList.toggle('sp-open',SP.on); SP.cv.style.display=SP.on?'block':'none'; document.getElementById('spBar').style.display=SP.on?'flex':'none';
  if(SP.on){ SP.draw=true; SP.erase=false; spLoad(); if(typeof kbHide==='function') kbHide(); } else { spSave(); }
  spUI();
}
(function(){ var f=document.createElement('button'); f.type='button'; f.id='spFab'; f.className='sp-fab'; f.innerHTML='✏️ <span>Scratchpad</span>'; f.title='Open a scratchpad to write your working'; f.addEventListener('click',function(){ spToggle(); }); document.body.appendChild(f); })();
var _rsSP = renderSlide;
renderSlide = function(){ _rsSP(); var fab=document.getElementById('spFab'); var q=!!swTab(); if(fab) fab.style.display=q?'':'none'; if(!q && SP.on) spToggle(false); if(SP.on) setTimeout(spLoad,30); };

renderLogin();
})();
</script>
</body>
</html>
