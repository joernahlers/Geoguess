<template>
    <div>
        <v-app-bar class="header-game" color="grey darken-4">
            <div
                id="countdown-timer"
                v-if="remainingTime != null && remainingTime > 0"
            >
                <span id="countdown-text">{{ countdownText }}</span>
            </div>
            <div id="moves" v-if="moves != null && moves >= 0">
                <span class="sub-text">{{ $t('HeaderGame.moves') }} : </span>
                <span class="main-text" id="moves-text"
                    >{{ move }} / {{ moves }}</span
                >
            </div>
            <div class="round-score-container room-name" v-if="roomName">
                <span class="sub-text">{{ $t('HeaderGame.room') }} : </span>
                <span class="main-text">{{ roomName }}</span>
            </div>
            <div class="flex-grow-1"></div>
            <div class="round-score-container">
                <span class="sub-text">{{ $t('HeaderGame.round') }}: </span>
            </div>
            <div>
                <span class="main-text" id="roundLabel"
                    >{{ round }} / {{ rounds }}</span
                >
            </div>
            <div class="round-score-container">
                <span class="sub-text">{{ $t('HeaderGame.distance') }}: </span>
            </div>
            <div>
                <span class="main-text">{{
                    $t('HeaderGame.kmaway', { value: score / 1000 })
                }}</span>
            </div>
            <div class="round-points-container">
                <span class="sub-text">{{ $t('HeaderGame.score') }}: </span>
            </div>
            <div>
                <span class="main-text">{{ points }}</span>
            </div>
        </v-app-bar>
    </div>
</template>

<script>
import { getCountdownText } from '@/utils';
export default {
    props: [
        'score',
        'points',
        'round',
        'remainingTime',
        'roomName',
        'rounds',
        'moves',
        'move',
    ],
    computed: {
        countdownText() {
            return getCountdownText(this.remainingTime);
        },
    },
};
</script>

<style scoped lang="scss">
.header-game {
    z-index: 3;
    opacity: 0.8;
}

.toolbar-title {
    color: white;
}

.round-score-container {
    padding: 0 10px 0 40px;
}

.round-points-container {
    padding: 0 10px 0 40px;
}

.main-text,
#countdown-text {
    color: white;
}

.sub-text {
    color: #616161;
}
@media (max-width: 450px) {
    .main-text,
    .sub-text,
    #countdown-text {
        font-size: 14px;
    }

    .round-score-container {
        padding: 0 5%;
        .sub-text {
            display: none;
        }
    }

    .round-points-container {
        padding: 0 5%;
        .sub-text {
            display: none;
        }
    }
}

@media (max-width: 555px) {
    .room-name {
        display: none;
    }
}
</style>
