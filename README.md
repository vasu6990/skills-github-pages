.flag__birthday .flag__left {
    transform: rotate(-10deg) translate(-119px,3px);
}

.flag__birthday .flag__right {
    transform: rotate(10deg) translate(-106px,39px) scaleX(-1);
}

.content {
    width: 100%;
    position: relative;
    display: flex;
    flex-direction: column;
    justify-content: center;
    gap: 25px;
    align-items: center;
    padding-top: 2rem;
}

.title {
    position: relative;
    width: 100%;
    display: flex;
    justify-content: center;
    font-family: "Titan One", sans-serif;
    font-size: 1.5rem;
    letter-spacing: 8px;
    flex-direction: column;
    perspective: 1000px;
}

#btn__letter {
    position: relative;
    margin-top: 17px;
    width: 209px;
    background-color: var(--color-text-pink);
    outline: none;
    padding: 6px 4px;
    font-size: 1rem;
    border-radius: 50px;
    border: 3px solid var(--color-black);
    font-family: "Sriracha", cursive;
    display: flex;
    align-items: center;
    justify-content: center;
    cursor: pointer;
    z-index: 2;
    /* transform: scale(1); */
    transition: all .5s ease-in-out;
}

.cricle {
    position: absolute;
    top: 10px;
    right: -54px;
    display: flex;
    justify-content: center;
    align-items: center;
    transform: scale(0);
    animation: scaleCricle 3s 15s forwards ease-in-out;
}

.title .hat {
    position: absolute;
    right: -98px;
    top: -51px !important;
    transform: rotate(-40deg);
    z-index: -1;
    animation: topHat 4s 7s forwards ease;
}

.box__letter .letter__border {
    position: absolute;
    width: 90vw;
    height: 315px;
    background-color: var(--color-white);
    border-radius: 27px;
    padding: 17px;
    box-shadow: rgba(0, 0, 0, 0.24) 0px 3px 8px;
    top: 50%;
    left: 50%;
    transform: translate(-50%,-50%);
    display: none;
}

.letter__border .letter {
    width: 100%;
    height: 100%;
    background-color: var(--color-bg-letter);
    border-radius: 10px;
    padding-top: 15px;
}

.letter__border .letter .title__letter {
    text-align: center;
    font-family: 'Dancing Script', cursive;
    font-weight: bold;
    font-size: 1.4rem;
}

.letter__border .letter .content__letter {
    position: relative;
    width: 100%;
    height: 100%;
    display: flex;
    padding-top: .7rem;
    padding-bottom: 70px;
}

.content__letter .right .text__letter {
    margin-top: -14px;
    padding: 20px 15px 10px 15px;
    font-family: 'Dancing Script', cursive;
    font-size: .8rem;
}

.content__letter .right .love__img {
    opacity: 0;
    position: absolute;
    right: 126px;
    top: 167px;
}

.love__img img {

        width: 84px;

}

.content .right .image {
    position: relative;
    width: 200px;
    height: 200px;
    border-radius: 50%;
    overflow: hidden;
    display: flex;
    align-items: center;
    border: 6px solid var(--color-black);
}

.name {
    position: absolute;
    padding: 0px 3px;
    bottom: -6px;
    border: 3px solid var(--color-black);
}

.name span {
    font-size: 1rem;
}

.right .balloon_one {
    position: absolute;
    top: 10px;
    left: -77px;
    animation: balloon1 2s infinite linear;
}

.right .balloon_one img{
    width: 76px !important;
}
