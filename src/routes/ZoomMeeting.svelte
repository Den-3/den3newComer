<script>
    import HoverButton from "$lib/component/HoverButton.svelte";

    import { onMount } from "svelte";
    import { slide } from "svelte/transition";
    const meetingDatas = [
        {
            title: "第1回",
            date: "4/8(水) 20:00~",
            content: "2026年度 電子計算機研究会 新入生説明会",
            meetingUrl: "https://shibaura-it.zoom.us/j/98258863232"
        },
        {
            title: "第2回",
            date: "4/17(金) 20:00~",
            content: "2026年度 電子計算機研究会 新入生説明会",
            meetingUrl: "https://shibaura-it.zoom.us/j/99543739567"
        },
        {
            title: "第3回",
            date: "4/24(金) 20:00~",
            content: "2026年度 電子計算機研究会 新入生説明会",
            meetingUrl: "https://shibaura-it.zoom.us/j/91386589930"
        },
    ]
    let index = $state(0)
</script>


<h2>Zoom説明会日程</h2>
<p>2026年度の説明会はZoomで行います．全3回を予定</p>
<p>セキュリティのため、今回の説明会は大学のアカウントに限定しています。</p>
<p>サインインするところでSSOを選択し、shibaura-itでサインインしてください</p>
<p>※個人のアカウント（通常のGmailなど）では参加できない設定になっていますのでご注意ください。</p>
<div class="buttons">
    {#each meetingDatas as meeting, i}
        <HoverButton text={meeting.title} isSelected={i === index} onclick={() => {index = i}}></HoverButton>
    {/each}
</div>
{#key index}
    <section>
        <h3>{meetingDatas[index].content}</h3>
        <p>{meetingDatas[index].date}</p>
        <a href={meetingDatas[index].meetingUrl} target="_blank">ZoomMeetingに参加する</a>
    </section>
{/key}


<p>電算はいつでも新入部員を歓迎します．メールで連絡いただければ，対応いたします．</p>
<p>Zoom説明会に参加できない方は相談からでも連絡いただいて大丈夫です．</p>
<div class="email-box">電算公式メールアドレス：<br><strong>den3.shibaura@gmail.com</strong></div>

<p>また、電算の活動内容ついては、こちらの紹介動画でもご覧いただけます．</p>
<div class="youtube">
    <p>
        <iframe width="560" height="315" src="https://www.youtube.com/embed/7EBLi26g6Xs?si=30zcjFRW1hO9gNIm" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
    </p>
</div>

<style>
    .email-box {
        background-color: #e3f2fd;
        padding: 1rem;
        border-radius: 8px;
        text-align: center;
        margin-top: 1rem;
        word-break: break-all;
    }
    
    .buttons {
        display: flex;
        justify-content: center;
        width: 100%;
        background-color: #e3f2fd;
        padding-bottom: 5px;
    }

    section {
        background-color: rgb(250, 250, 250);
        padding: 1.5rem;
        margin-bottom: 1.5rem;
    }

    h2 {
        border-left: 5px solid #007BFF;
        padding-left: 0.5rem;
        margin-bottom: 1rem;
    }

    embed {
        width: 100%;
        aspect-ratio: 16/10;
    }

    .youtube{
        width: 100%;
        max-width: 570px;
        aspect-ratio: 16 / 9;
        margin: 0 auto;
    }

    .youtube iframe{
        width: 100%;
        border: none;
    }
</style>
