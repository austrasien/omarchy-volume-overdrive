# v2.3.1 — No more stuck launch OSD on the day line

- The OSD close now goes through the same ordered queue as the show sent to the day line. Before, a close could reach `austraz.dayline` ahead of a show still in flight, and a duration-0 card (such as "Launching …" while an app starts) stayed on screen for good.
