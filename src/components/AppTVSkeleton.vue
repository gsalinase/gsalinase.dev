<template>
    <div>
      <div class="box"></div>
      <svg class="noise">
        <filter id="noise">
          <feTurbulence id="turbulence">
            <animate
              attributeName="baseFrequency"
              dur="50s"
              values="0.9 0.9;0.8 0.8; 0.9 0.9"
              repeatCount="indefinite"
            ></animate>
          </feTurbulence>
          <feDisplacementMap in="SourceGraphic" scale="60"></feDisplacementMap>
        </filter>
      </svg>
    </div>
</template>

<style lang="css" scoped>
.box {
  position: absolute;
  top: -50px;
  left: -50px;
  width: calc(100% + 50px);
  height: calc(100% + 50px);
  background: repeating-linear-gradient(#111, #111 50%, white 50%, white);
  background-size: 5px 5px;
  filter: url(#noise);
}

.noise {
  width: 0;
  height: 0;
}
</style>