<template>
  <div class="jcunhafonte-welcome">
    <div class="jcunhafonte-welcome__background" v-bind:style="style"></div>
    <div class="jcunhafonte-welcome__content">
      <h1 v-text="title"></h1>
      <p v-text="job"></p>
      <p v-text="hobbies"></p>
    </div>
    <div class="jcunhafonte-welcome__socials">
      <ul>
        <li v-for="social in socials">
          <a v-bind:href="social.name === 'email' ? `mailto:${social.href}` : social.href"
             v-bind:target="social.name === 'email' ? '_self' : '_blank'">{{social.name}}</a>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'welcome',
    data () {
      return {
        title: 'José Cunha Fonte',
        job: 'software engineer, writer, speaker',
        hobbies: 'surf, nature, music, animals',
        socials: [
          {
            name: 'linkedin',
            href: 'https://www.linkedin.com/in/jcunhafonte'
          },
          {
            name: 'github',
            href: 'https://github.com/jcunhafonte'
          },
          {
            name: 'twitter',
            href: 'https://twitter.com/jcunhafonte'
          },
          {
            name: 'email',
            href: 'jcunhafonte@gmail.com'
          }
        ],
        background: {
          step: 0,
          colors: [
            [62, 35, 255],
            [60, 255, 60],
            [255, 35, 98],
            [45, 175, 230],
            [255, 0, 255],
            [255, 128, 0]
          ],
          speed: 0.002,
          colorIndices: [0, 1, 2, 3],
          values: {}
        }
      }
    },
    methods: {
      updateBackground () {
        const colorZeroZero = this.background.colors[this.background.colorIndices[0]]
        const colorZeroOne = this.background.colors[this.background.colorIndices[1]]
        const colorOneZero = this.background.colors[this.background.colorIndices[2]]
        const colorOneOne = this.background.colors[this.background.colorIndices[3]]

        const istep = 1 - this.background.step

        const rgbs = [
          {
            r: Math.round(istep * colorZeroZero[0] + this.background.step * colorZeroOne[0]),
            g: Math.round(istep * colorZeroZero[1] + this.background.step * colorZeroOne[1]),
            b: Math.round(istep * colorZeroZero[2] + this.background.step * colorZeroOne[2])
          },
          {
            r: Math.round(istep * colorOneZero[0] + this.background.step * colorOneOne[0]),
            g: Math.round(istep * colorOneZero[1] + this.background.step * colorOneOne[1]),
            b: Math.round(istep * colorOneZero[2] + this.background.step * colorOneOne[2])
          }
        ]
        const colors = [`rgb(${rgbs[0].r}, ${rgbs[0].g}, ${rgbs[0].b})`, `rgb(${rgbs[1].r}, ${rgbs[1].g}, ${rgbs[1].b})`]

        this.background.values = {
          'background': `linear-gradient(to right, ${colors[0]}, ${colors[1]})`,
          // eslint-disable-next-line no-dupe-keys
          'background': `-moz-linear-gradient(left, ${colors[0]} 0%, ${colors[1]} 100%)`,
          // eslint-disable-next-line no-dupe-keys
          'background': `-o-linear-gradient(right, ${colors[0]}, ${colors[1]})`,
          // eslint-disable-next-line no-dupe-keys
          'background': `linear-gradient(to right, ${colors[0]}, ${colors[1]})`
        }

        this.background.step += this.background.speed

        if (this.background.step >= 1) {
          this.background.step %= 1
          this.background.colorIndices[0] = this.background.colorIndices[1]
          this.background.colorIndices[2] = this.background.colorIndices[3]
          this.background.colorIndices[1] = (this.background.colorIndices[1] + Math.floor(1 + Math.random() * (this.background.colors.length - 1))) % this.background.colors.length
          this.background.colorIndices[3] = (this.background.colorIndices[3] + Math.floor(1 + Math.random() * (this.background.colors.length - 1))) % this.background.colors.length
        }
      }
    },
    computed: {
      style () {
        return this.background.values
      }
    },
    mounted () {
      setInterval(() => this.updateBackground(), 15)
    }
  }
</script>

<style lang="scss" scoped>
  @import "../styles/colors";

  .jcunhafonte-welcome {
    &__background {
      position: absolute;
      width: 100%;
      height: 100%;
    }

    &__content {
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
      text-align: center;
      width: 100%;

      h1 {
        font-size: 42px;
        margin: 0;
        text-transform: uppercase;
        letter-spacing: 2px;
        word-spacing: 4px;

        @media screen and (max-width: 480px) {
          font-size: 24px
        }
      }

      p {
        font-size: 18px;
        margin-top: 30px;

        &:last-child {
          margin-top: 10px;
        }

        @media screen and (max-width: 480px) {
          font-size: 16px
        }
      }
    }

    &__socials {
      position: absolute;
      width: 100%;
      bottom: 40px;

      ul {
        list-style: none;
        display: flex;
        justify-content: center;
        margin: 0;
        padding: 0;

        li {
          margin: 0 10px;

          a {
            color: $white;
            text-decoration: none;
          }
        }
      }
    }
  }
</style>
