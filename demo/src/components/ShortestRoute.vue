<template>
  <div>
    <h2>Fastest route is:</h2>
    Mäntytie 7 -> Urheilukatu 23 -> Somerotie 1 -> Näkinkuja 6 -> Museokatu 23
    -> Toimintakeidas

    <h4>Total time: {{ fastestRoute.duration }}</h4>
  </div>
</template>

<script setup>
import { onMounted } from "vue";

const durations = {
  A: { A: 0, B: 246.3, C: 489.6, D: 389, E: 626.1, X: 516.9 },
  B: { A: 236.9, B: 0, C: 378.9, D: 316.6, E: 450.9, X: 402.5 },
  C: { A: 518.6, B: 414.2, C: 0, D: 516.9, E: 378.2, X: 602.8 },
  D: { A: 337, B: 265.9, C: 413.2, D: 0, E: 440.5, X: 234.7 },
  E: { A: 650.2, B: 485, C: 376.1, D: 496.2, E: 0, X: 328.9 },
  X: { A: 551.6, B: 462.6, C: 610.1, D: 236.9, E: 315.8, X: 0 },
};

const fastestRoute = allRoutes.reduce((previous, current) => {
  return current.duration < previous.duration ? current : previous;
});

onMounted(() => {
  console.log({
    A: "Mäntytie 7",
    B: "Urheilukatu 23",
    C: "Somerontie 1",
    D: "Museokatu 23",
    E: "Näkinkuja 6",
    X: "Toimintakeidas",
  });
  console.log("Customers wishes for the route: ", {
    customer1: "A -> B -> X",
    customer2: "C -> D -> X",
    customer3: "E -> X",
  });
  console.log("All possible routes: ", allRoutes);
  console.log("Fastest route:", fastestRoute);
});

const allRoutes = [
  {
    route: "AB CE DX",
    duration:
      durations.A.B +
      durations.B.C +
      durations.C.E +
      durations.E.D +
      durations.D.X,
  },
  {
    route: "AB CD EX",
    duration:
      durations.A.B +
      durations.B.C +
      durations.C.D +
      durations.D.E +
      durations.E.X,
  },
  {
    route: "AB EC DX",
    duration:
      durations.A.B +
      durations.B.E +
      durations.E.C +
      durations.C.D +
      durations.D.X,
  },

  {
    route: "AC EB DX",
    duration:
      durations.A.C +
      durations.C.E +
      durations.E.B +
      durations.B.D +
      durations.D.X,
  },
  {
    route: "AC ED BX",
    duration:
      durations.A.C +
      durations.C.E +
      durations.E.D +
      durations.D.B +
      durations.B.X,
  },
  {
    route: "AC DB EX",
    duration:
      durations.A.C +
      durations.C.D +
      durations.D.B +
      durations.B.E +
      durations.E.X,
  },
  {
    route: "AC DE BX",
    duration:
      durations.A.C +
      durations.C.D +
      durations.D.E +
      durations.E.B +
      durations.B.X,
  },
  {
    route: "AC BD EX",
    duration:
      durations.A.C +
      durations.C.B +
      durations.B.D +
      durations.D.E +
      durations.E.X,
  },
  {
    route: "AC BE DX",
    duration:
      durations.A.C +
      durations.C.B +
      durations.B.E +
      durations.E.D +
      durations.D.X,
  },

  {
    route: "AE CB DX",
    duration:
      durations.A.E +
      durations.E.C +
      durations.C.B +
      durations.B.D +
      durations.D.X,
  },
  {
    route: "AE CD BX",
    duration:
      durations.A.E +
      durations.E.C +
      durations.C.D +
      durations.D.B +
      durations.B.X,
  },
  {
    route: "AE BC DX",
    duration:
      durations.A.E +
      durations.E.B +
      durations.B.C +
      durations.C.D +
      durations.D.X,
  },

  {
    route: "CD EA BX",
    duration:
      durations.C.D +
      durations.D.E +
      durations.E.A +
      durations.A.B +
      durations.B.X,
  },
  {
    route: "CD AE BX",
    duration:
      durations.C.D +
      durations.D.A +
      durations.A.E +
      durations.E.B +
      durations.B.X,
  },
  {
    route: "CD AB EX",
    duration:
      durations.C.D +
      durations.D.A +
      durations.A.B +
      durations.B.E +
      durations.E.X,
  },

  {
    route: "CA BD EX",
    duration:
      durations.C.A +
      durations.A.B +
      durations.B.D +
      durations.D.E +
      durations.E.X,
  },
  {
    route: "CA BE DX",
    duration:
      durations.C.A +
      durations.A.B +
      durations.B.E +
      durations.E.D +
      durations.D.X,
  },
  {
    route: "CA DB EX",
    duration:
      durations.C.A +
      durations.A.D +
      durations.D.B +
      durations.B.E +
      durations.E.X,
  },
  {
    route: "CA DE BX",
    duration:
      durations.C.A +
      durations.A.D +
      durations.D.E +
      durations.E.B +
      durations.B.X,
  },
  {
    route: "CA EB DX",
    duration:
      durations.C.A +
      durations.A.E +
      durations.E.B +
      durations.B.D +
      durations.D.X,
  },
  {
    route: "CA ED BX",
    duration:
      durations.C.A +
      durations.A.E +
      durations.E.D +
      durations.D.B +
      durations.B.X,
  },

  {
    route: "CE AB DX",
    duration:
      durations.C.E +
      durations.E.A +
      durations.A.B +
      durations.B.D +
      durations.D.X,
  },
  {
    route: "CE DA BX",
    duration:
      durations.C.E +
      durations.E.D +
      durations.D.A +
      durations.A.B +
      durations.B.X,
  },
  {
    route: "CE AD BX",
    duration:
      durations.C.E +
      durations.E.A +
      durations.A.D +
      durations.D.B +
      durations.B.X,
  },

  {
    route: "EA BC DX",
    duration:
      durations.E.A +
      durations.A.B +
      durations.B.C +
      durations.C.D +
      durations.D.X,
  },
  {
    route: "EA CB DX",
    duration:
      durations.E.A +
      durations.A.C +
      durations.C.B +
      durations.B.D +
      durations.D.X,
  },
  {
    route: "EA CD BX",
    duration:
      durations.E.A +
      durations.A.C +
      durations.C.D +
      durations.D.B +
      durations.B.X,
  },

  {
    route: "EC AB DX",
    duration:
      durations.E.C +
      durations.C.A +
      durations.C.B +
      durations.B.D +
      durations.D.X,
  },
  {
    route: "EC DA BX",
    duration:
      durations.E.C +
      durations.C.D +
      durations.D.A +
      durations.A.B +
      durations.B.X,
  },
  {
    route: "EC AD BX",
    duration:
      durations.E.C +
      durations.C.A +
      durations.A.D +
      durations.D.B +
      durations.B.X,
  },
];
</script>
